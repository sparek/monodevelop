
ADDIN_BUILD = $(top_builddir)/build/AddIns/VersionControl
ASSEMBLY = $(ADDIN_BUILD)/MonoDevelop.VersionControl.Git.dll
NGIT=$(top_builddir)/../external/ngit/bin/NGit.dll
NSCH=$(top_builddir)/../external/ngit/bin/NSch.dll
SHARPEN=$(top_builddir)/../external/ngit/bin/Sharpen.dll

DEPS =  \
	$(top_builddir)/build/AddIns/VersionControl/MonoDevelop.VersionControl.dll \
	$(top_builddir)/build/bin/ICSharpCode.NRefactory.CSharp.dll \
	$(top_builddir)/build/bin/ICSharpCode.NRefactory.dll \
	$(top_builddir)/build/bin/Mono.TextEditor.dll \
	$(top_builddir)/build/bin/MonoDevelop.Core.dll \
	$(top_builddir)/build/bin/MonoDevelop.Ide.dll \
	$(top_builddir)/../external/ngit/bin/NGit.dll \
	$(top_builddir)/../external/ngit/bin/NSch.dll \
	$(top_builddir)/../external/ngit/bin/Sharpen.dll

REFS =  \
	$(GLIB_SHARP_LIBS) \
	$(GTK_SHARP_LIBS) \
	-r:Mono.Posix \
	-r:System \
	-r:System.Core

FILES =  \
	AssemblyInfo.cs \
	gtk-gui/generated.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.ConflictResolutionDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.CredentialsDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.EditBranchDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.EditRemoteDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.GitCommitDialogExtensionWidget.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.GitConfigurationDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.GitOptionsPanelWidget.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.MergeDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.NewStashDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.PushDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.StashManagerDialog.cs \
	gtk-gui/MonoDevelop.VersionControl.Git.UserInfoConflictDialog.cs \
	MonoDevelop.VersionControl.Git/Commands.cs \
	MonoDevelop.VersionControl.Git/ConflictResolutionDialog.cs \
	MonoDevelop.VersionControl.Git/CredentialsDialog.cs \
	MonoDevelop.VersionControl.Git/EditBranchDialog.cs \
	MonoDevelop.VersionControl.Git/EditRemoteDialog.cs \
	MonoDevelop.VersionControl.Git/FilteredStatus.cs \
	MonoDevelop.VersionControl.Git/GitClient.cs \
	MonoDevelop.VersionControl.Git/GitCommitDialogExtension.cs \
	MonoDevelop.VersionControl.Git/GitCommitDialogExtensionWidget.cs \
	MonoDevelop.VersionControl.Git/GitConfigurationDialog.cs \
	MonoDevelop.VersionControl.Git/GitCredentials.cs \
	MonoDevelop.VersionControl.Git/GitNodeBuilderExtension.cs \
	MonoDevelop.VersionControl.Git/GitOptionsPanel.cs \
	MonoDevelop.VersionControl.Git/GitOptionsPanelWidget.cs \
	MonoDevelop.VersionControl.Git/GitRepository.cs \
	MonoDevelop.VersionControl.Git/GitService.cs \
	MonoDevelop.VersionControl.Git/GitSupportFeature.cs \
	MonoDevelop.VersionControl.Git/GitUtil.cs \
	MonoDevelop.VersionControl.Git/GitVersionControl.cs \
	MonoDevelop.VersionControl.Git/MergeDialog.cs \
	MonoDevelop.VersionControl.Git/NewStashDialog.cs \
	MonoDevelop.VersionControl.Git/PushDialog.cs \
	MonoDevelop.VersionControl.Git/Stash.cs \
	MonoDevelop.VersionControl.Git/StashManagerDialog.cs \
	MonoDevelop.VersionControl.Git/UserInfoConflictDialog.cs

RES =  \
	gtk-gui/gui.stetic \
	icons/arrow_branch.png \
	icons/server.png \
	icons/tag_blue.png \
	MonoDevelop.VersionControl.Git.addin.xml

$(ASSEMBLY): $(build_sources) $(build_resources) $(DEPS)
	mkdir -p $(ADDIN_BUILD)
	cp $(NGIT) $(ADDIN_BUILD)
	cp $(NGIT).mdb $(ADDIN_BUILD) || true 
	cp $(NSCH) $(ADDIN_BUILD)
	cp $(NSCH).mdb $(ADDIN_BUILD) || true
	cp $(SHARPEN) $(ADDIN_BUILD)
	cp $(SHARPEN).mdb $(ADDIN_BUILD) || true
	$(CSC) $(CSC_FLAGS) $(build_sources) $(REFS) $(build_deps) $(build_resources:%=/resource:%) -out:$@ -target:library

$(ASSEMBLY).mdb: $(ASSEMBLY)

CLEANFILES = $(ASSEMBLY) $(ASSEMBLY).mdb $(ADDIN_BUILD)/NGit.dll $(ADDIN_BUILD)/NSch.dll $(ADDIN_BUILD)/Sharpen.dll
EXTRA_DIST = $(FILES) $(RES)

if ENABLE_GIT
all: $(ASSEMBLY) $(ASSEMBLY).mdb
else
all:
endif

if ENABLE_GIT
addindir = $(MD_ADDIN_DIR)/VersionControl
addin_DATA = $(ASSEMBLY) $(ASSEMBLY).mdb $(ADDIN_BUILD)/NGit.dll $(ADDIN_BUILD)/NGit.dll.mdb $(ADDIN_BUILD)/NSch.dll $(ADDIN_BUILD)/NSch.dll.mdb $(ADDIN_BUILD)/Sharpen.dll $(ADDIN_BUILD)/Sharpen.dll.mdb
endif

include $(top_srcdir)/Makefile.include
