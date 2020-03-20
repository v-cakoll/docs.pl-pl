---
title: Przestarzałe typy w ramach .NET
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
ms.openlocfilehash: b7932a553f39e1f1da2a3946878d6224099da8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802690"
---
# <a name="obsolete-types-in-the-net-framework"></a>Przestarzałe typy w ramach .NET

<a name="introduction"></a>Tabele w tym artykule listy typów, które są przestarzałe w .NET Framework 4.5 i .NET Framework 4.6, zorganizowane według zestawu. Skorzystaj z poniższych łączy, aby wyświetlić listę przestarzałych typów i zalecanych alternatyw w każdym zestawie. Ponieważ te typy są przestarzałe, wszystkie ich elementy członkowskie są również przestarzałe. Aby uzyskać listę dodatkowych przestarzałych elementów członkowskich w bibliotece klas .NET Framework, zobacz [Przestarzałe elementy członkowskie](obsolete-members.md).

- [Przestarzałe typy w zespołach systemowych](#obsolete_types_in_system_assemblies)

  - [mscorlib.dll](#mscorlib)

  - [System.Core.dll](#Core)

  - [System.Data.dll](#data)

  - [System.Data.OracleClient.dll](#oracleclient)

  - [Plik System.Design.dll](#design)

  - [PLik System.dll](#system)

  - [System.EnterpriseServices.dll](#enterpriseservices)

  - [System.Net.dll](#net)

  - [System.ServiceModel.dll](#servicemodel)

  - [System.web.dll](#web)

  - [Plik www.Mobile.dll](#mobile)

  - [Plik System.Workflow.Activities.dll](#workflow_activities)

  - [Plik System.Workflow.ComponentModel.dll](#workflow_componentmodel)

  - [Plik System.Workflow.Runtime.dll](#workflow_runtime)

  - [Plik System.WorkflowServices.dll](#workflowservices)

  - [Plik System.Xaml.dll](#xaml)

  - [System.Xml.dll](#xml)

  - [Windowsbase.dll](#WindowsBase)

- [Przestarzałe typy w zestawach firmy Microsoft](#obsolete_types_in_microsoft_assemblies)

  - [IEHost.dll i IEExec.exe](#IEHost)

  - [Plik Microsoft.Build.Engine.dll](#Engine)

  - [Plik dll języka Microsoft.JScript](#jscript)

  - [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)

  - [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)

  - [Microsoft.VisualC.dll](#visualc)

<a name="obsolete_types_in_system_assemblies"></a>

## <a name="obsolete-types-in-system-assemblies"></a>Przestarzałe typy w zestawach systemowych

W poniższych tabelach przedstawiono typy, które zostały uznane za przestarzałe w zestawach systemowych. Te zestawy są używane\-do tworzenia aplikacji ogólnego przeznaczenia, który jest przeznaczony dla programu .NET Framework.

<a name="mscorlib"></a>

### <a name="assembly-mscorlibdll"></a>Montaż: mscorlib.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Ten typ wcześniej wskazywał nieokreślony błąd krytyczny w czasie wykonywania. Środowisko wykonawcze nie zgłasza już tego wyjątku, więc ten typ jest przestarzały.|
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Użyj <xref:System.StringComparer?displayProperty=nameWithType> zamiast tego.|
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Użyj <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType> zamiast tego.|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|Klasa <xref:System.Configuration.Assemblies.AssemblyHash> została przestarzała.|
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5. Zamiast <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> tego należy użyć tej klasy w obszarze nazw System.Runtime.CompilerServices.|
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|Dostępny jest alternatywny interfejs <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> API: zamiast tego emituj atrybut niestandardowy.|
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Ten atrybut jest przestarzały i zostanie usunięty w przyszłej wersji.|
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|Jest <xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> przestarzały.|
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Ten atrybut został przestarzały. Domeny aplikacji nie są już zgodne z granicami kontekstu aktywacji w wywołaniach IDispatch.|
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=nameWithType>|Zamiast tego użyj polecenia cmdlet <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=nameWithType>.|
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope>jest używany tylko dla zgodności przezroczystości .NET 2.0.|
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute>jest używany tylko dla zgodności przezroczystości .NET 2.0. Zamiast tego <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType> użyj.|
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Ten typ jest przestarzały i zostanie usunięty w przyszłej wersji programu .NET Framework.|
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|Poziom zestawu deklaratywne zabezpieczeń jest przestarzały i nie jest już domyślnie wymuszane przez CLR.|
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Ten typ jest przestarzały i zostanie usunięty w przyszłej wersji programu .NET Framework.|

[Powrót do początku](#introduction)

<a name="Core"></a>

### <a name="assembly-systemcoredll"></a>Montaż: System.Core.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|Użycie tego typu generuje błąd kompilatora.<br /><br /> Nie należy używać tego typu.|

[Powrót do początku](#introduction)

<a name="data"></a>

### <a name="assembly-systemdatadll"></a>Montaż: System.Data.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute>Zdeprecjonowana.|
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes>Zdeprecjonowana.|
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|Klasa <xref:System.Data.TypedDataSetGenerator> zostanie usunięta w przyszłej wersji. Użyj <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> w pliku System.Design.dll.|
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|Klasa <xref:System.Xml.XmlDataDocument> zostanie usunięta w przyszłej wersji.|

[Powrót do początku](#introduction)

<a name="oracleclient"></a>

### <a name="assembly-systemdataoracleclientdll"></a>Montaż: System.Data.OracleClient.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory>Zdeprecjonowana.|
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand>Zdeprecjonowana.|
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder>Zdeprecjonowana.|
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection>Zdeprecjonowana.|
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder>Zdeprecjonowana.|
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter>Zdeprecjonowana.|
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission>Zdeprecjonowana.|
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>Zdeprecjonowana.|

[Powrót do początku](#introduction)

<a name="design"></a>

### <a name="assembly-systemdesigndll"></a>Montaż: System.Design.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Ta klasa została przestarzała. Zamiast tego użyj polecenia cmdlet <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ databindings edycji jest uruchamiany za pośrednictwem <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> zamiast siatki właściwości.|
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ databindings edycji jest uruchamiany za pośrednictwem <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> zamiast siatki właściwości.|
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> i <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> i <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>edycja szablonu jest obsługiwana w pliku . Aby obsługiwać edycję szablonu, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> udostępnij <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>dane szablonu we właściwości i zadzwoń .|
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. Zawiera <xref:System.Web.UI.Design.WebFormsReferenceManager> dodatkowe funkcje i pozwala na większą rozszerzalność. Aby uzyskać <xref:System.Web.UI.Design.WebFormsReferenceManager>, `RootDesigner.ReferenceManager` użyj właściwości <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>z .|
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. Zawiera <xref:System.Web.UI.Design.WebFormsRootDesigner> dodatkowe funkcje i pozwala na większą rozszerzalność. Aby uzyskać <xref:System.Web.UI.Design.WebFormsRootDesigner>, <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> użyj właściwości <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>z .|
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>edycja szablonu jest obsługiwana w pliku . Aby obsługiwać edycję szablonu, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> udostępnij <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>dane szablonu we właściwości i zadzwoń .|
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|Zalecaną alternatywą <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> jest to, że używa do edycji zawartości. Regiony projektanta umożliwiają lepszą kontrolę nad edytowanym zawartością.|
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>edycja szablonu jest obsługiwana w pliku . Aby obsługiwać edycję szablonu, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> udostępnij <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>dane szablonu we właściwości i zadzwoń .|
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>edycja szablonu jest obsługiwana w pliku . Aby obsługiwać edycję szablonu, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> udostępnij <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>dane szablonu we właściwości i zadzwoń .|
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ autoformatowanie jest uruchamiane przez hosta projektanta. Lista dostępnych autoformatów jest widoczna <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> we właściwości.|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|Zalecaną alternatywą <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType> <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> jest to, że używa do edycji zawartości. Regiony projektanta umożliwiają lepszą kontrolę nad edytowanym zawartością.|

[Powrót do początku](#introduction)

<a name="system"></a>

### <a name="assembly-systemdll"></a>Montaż: System.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Ten interfejs został przestarzały. Zamiast <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> tego dodaj <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> typ do obsługi.|
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Zamiast <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> tego użyj do pracy z nowym modelem ustawień.|
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Ten atrybut został przestarzały. Zamiast tego użyj polecenia cmdlet <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType>.|
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Ta klasa została przestarzała.|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Ta klasa została przestarzała. Zamiast tego należy użyć <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> liczników wydajności za pośrednictwem klasy.|
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Ta klasa została przestarzała. Zamiast <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> tego użyj dostępu i ustawienia globalnego domyślnego serwera proxy. Użyj "null" zamiast <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>.|
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|

[Powrót do początku](#introduction)

<a name="enterpriseservices"></a>

### <a name="assembly-systementerpriseservicesdll"></a>Montaż: System.EnterpriseServices.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|Klasa <xref:System.EnterpriseServices.RegistrationHelperTx> została przestarzała.|

[Powrót do początku](#introduction)

<a name="net"></a>

### <a name="assembly-systemnetdll"></a>Montaż: System.Net.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|

[Powrót do początku](#introduction)

<a name="servicemodel"></a>

### <a name="assembly-systemservicemodeldll"></a>Montaż: System.ServiceModel.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Funkcja kanału równorzędnego jest przestarzała i zostanie usunięta w przyszłości.|
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Ten typ jest przestarzały. Aby włączyć <xref:System.Net.CookieContainer>funkcję `AllowCookies` Http , użyj właściwości <xref:System.ServiceModel.Channels.HttpTransportBindingElement>na powiązaniu Http lub na .|
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Funkcja kanału równorzędnego jest przestarzała i zostanie usunięta w przyszłości.|
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Funkcja kanału równorzędnego jest przestarzała i zostanie usunięta w przyszłości.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Funkcja kanału równorzędnego jest przestarzała i zostanie usunięta w przyszłości.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Funkcja kanału równorzędnego jest przestarzała i zostanie usunięta w przyszłości.|
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Funkcja kanału równorzędnego jest przestarzała i zostanie usunięta w przyszłości.|
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Funkcja kanału równorzędnego jest przestarzała i zostanie usunięta w przyszłości.|

[Powrót do początku](#introduction)

<a name="web"></a>

### <a name="assembly-systemwebdll"></a>Montaż: System.Web.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania paszportowego nie jest już obsługiwany i został zastąpiony przez [konto Microsoft](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania paszportowego nie jest już obsługiwany i został zastąpiony przez [konto Microsoft](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania paszportowego nie jest już obsługiwany i został zastąpiony przez [konto Microsoft](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania paszportowego nie jest już obsługiwany i został zastąpiony przez [konto Microsoft](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania paszportowego nie jest już obsługiwany i został zastąpiony przez [konto Microsoft](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania paszportowego nie jest już obsługiwany i został zastąpiony przez [konto Microsoft](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Convert?displayProperty=nameWithType> i <xref:System.String.Format%2A?displayProperty=nameWithType>.|

[Powrót do początku](#introduction)

<a name="mobile"></a>

### <a name="assembly-systemwebmobiledll"></a>Montaż: System.Web.Mobile.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll został przestarzały i nie powinien być już używany. Aby uzyskać informacje na temat tworzenia aplikacji mobilnych ASP.NET, zobacz [ASP.NET dla telefonów komórkowych](/aspnet/mobile/overview).|

[Powrót do początku](#introduction)

<a name="workflow_activities"></a>

### <a name="assembly-systemworkflowactivitiesdll"></a>Zestaw: System.Workflow.Activities.dll

|Typ|Komunikat|
|----------|-------------|
|Wszystkie typy <xref:System.Workflow.Activities?displayProperty=nameWithType> w obszarze nazw|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|

[Powrót do początku](#introduction)

<a name="workflow_componentmodel"></a>

### <a name="assembly-systemworkflowcomponentmodeldll"></a>Montaż: System.Workflow.ComponentModel.dll

|Typ|Komunikat|
|----------|-------------|
|Wszystkie typy <xref:System.Workflow.ComponentModel> w <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> obszarze nazw z wyjątkiem<xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|Wszystkie typy <xref:System.Workflow.ComponentModel.Compiler> w <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> obszarze nazw z wyjątkiem<xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|Wszystkie typy <xref:System.Workflow.ComponentModel.Design> w obszarze nazw z wyjątkiem<xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|

[Powrót do początku](#introduction)

<a name="workflow_runtime"></a>

### <a name="assembly-systemworkflowruntimedll"></a>Zestaw: System.Workflow.Runtime.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Activities.Statements.Interop?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 są przestarzałe. Zamiast tego należy użyć typów przepływu pracy <xref:System.Activities>4.0 z programu . \*.|
|<xref:System.Activities.Tracking.InteropTrackingRecord?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 są przestarzałe. Zamiast tego należy użyć typów przepływu pracy <xref:System.Activities>4.0 z programu . \*.|
|Wszystkie typy <xref:System.Workflow.Runtime> w obszarze nazw|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|Wszystkie typy <xref:System.Workflow.Runtime.Configuration> w obszarze nazw|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|Wszystkie typy <xref:System.Workflow.Runtime.DebugEngine> w obszarze nazw z wyjątkiem<xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|Wszystkie typy <xref:System.Workflow.Runtime.Hosting> w obszarze nazw z wyjątkiem<xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|
|Wszystkie typy <xref:System.Workflow.Runtime.Tracking> w obszarze nazw|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Przepływ pracy system.work. \* są przestarzałe. Zamiast tego użyj nowych typów <xref:System.Activities>z . \*.|

[Powrót do początku](#introduction)

<a name="workflowservices"></a>

### <a name="assembly-systemworkflowservicesdll"></a>Montaż: System.WorkflowServices.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|Wszystkie typy <xref:System.Workflow.Activities?displayProperty=nameWithType> w obszarze nazw|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego, należy użyć nowych typów <xref:System.Activities>WF 4 z . \*.|

[Powrót do początku](#introduction)

<a name="xaml"></a>

### <a name="assembly-systemxamldll"></a>Montaż: System.Xaml.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|Nie jest używany przez analizatora XAML. Proszę spojrzeć na <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>.|

[Powrót do początku](#introduction)

<a name="xml"></a>

### <a name="assembly-systemxmldll"></a>Montaż: System.Xml.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|Pierwszy przestarzały w .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Służy <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> do kompilacji i sprawdzania poprawności schematu.|
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Użyj <xref:System.Xml.XmlReader?displayProperty=nameWithType> utworzonego <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> przez metodę <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> przy użyciu odpowiedniego zamiast tego.|
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|Użycie tego typu generuje błąd kompilatora. Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Ta klasa została przestarzała. Użyj <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType> zamiast tego.|

[Powrót do początku](#introduction)

<a name="WindowsBase"></a>

### <a name="assembly-windowsbasedll"></a>Montaż: WindowsBase.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>Zdeprecjonowana. Ten interfejs nie jest już używany.|

[Powrót do początku](#introduction)

<a name="obsolete_types_in_microsoft_assemblies"></a>

## <a name="obsolete-types-in-microsoft-assemblies"></a>Przestarzałe typy w zestawach firmy Microsoft

W poniższych sekcjach przedstawiono przestarzałe typy w zestawach firmy Microsoft. Zestawy te są zestawami specjalnego przeznaczenia, takimi jak zestawy przeznaczone dla poszczególnych języków (na przykład Microsoft.JScript.dll lub Microsoft.VisualC.dll).

<a name="IEHost"></a>

### <a name="assembly-iehostdll-and-ieexecexe"></a>Montaż: IEHost.dll i IEExec.exe

Zestawy IEHost.dll i IEExec.exe zostały usunięte z programu .NET Framework. Wszystkie ich typy i ich elementy członkowskie są przestarzałe i nie są obsługiwane od programu .NET Framework 4. Zestawy te były używane do obsługi formantów windows forms i uruchamiania plików wykonywalnych w programie Internet Explorer. Zalecane alternatywy obejmują ClickOnce, aplikacje przeglądarki XAML (XBAP) i Microsoft Silverlight.

[Powrót do początku](#introduction)

<a name="Engine"></a>

### <a name="assembly-microsoftbuildenginedll"></a>Montaż: Microsoft.Build.Engine.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Ta klasa została przestarzała. Użyj <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> z zestawu *Microsoft.Build* zamiast tego.|
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Ta klasa została przestarzała. Użyj <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> z zestawu *Microsoft.Build* zamiast tego.|

[Powrót do początku](#introduction)

<a name="jscript"></a>

### <a name="assembly-microsoftjscriptdll"></a>Montaż: Microsoft.JScript.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Ten typ został przestarzały w programie Visual Studio 2005; nie ma zamiennika dla tej funkcji. Dodatkowe informacje <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> można znaleźć w dokumentacji.|

[Powrót do początku](#introduction)

<a name="VBCompat"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Zestaw: Microsoft.VisualBasic.Compatibility.dll

Aby uzyskać informacje dotyczące migracji z języka Visual Basic 6, zobacz [Centrum zasobów języka Visual Basic 6.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-basic-6/visual-basic-6.0-documentation).

|Typ|Komunikat|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|

[Powrót do początku](#introduction)

<a name="VBCompatData"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>Zestaw: Microsoft.VisualBasic.Compatibility.Data.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=nameWithType>|Ten element członkowski jest przestarzały.|

[Powrót do początku](#introduction)

<a name="visualc"></a>

### <a name="assembly-microsoftvisualcdll"></a>Montaż: Microsoft.VisualC.dll

|Typ|Komunikat|
|----------|-------------|
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzałym zestawem i istnieje tylko dla zgodności z powrotem.|

## <a name="see-also"></a>Zobacz też

- [Przestarzałe elementy w ułatwieniach dostępu](whats-obsolete.md)
- [Przestarzali członkowie](obsolete-members.md)
