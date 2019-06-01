---
title: Przestarzałe typy w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a1243ad856bc5f8cc104c9f2e08fce515a849d8
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457058"
---
# <a name="obsolete-types-in-the-net-framework"></a>Przestarzałe typy w programie .NET Framework
<a name="introduction"></a> W tabelach, w tym artykule przedstawiono typy, które są przestarzałe w programie .NET Framework 4.5 i .NET Framework 4.6, uporządkowane według zestawu. Poniższe łącza umożliwiają wyświetlenie listy przestarzałych typów i zalecanych rozwiązań alternatywnych, w każdym zestawie. Ponieważ te typy są nieaktualne, ich elementów członkowskich również są nieaktualne. Aby uzyskać listę dodatkowych przestarzali członkowie w bibliotece klas programu .NET Framework, zobacz [Przestarzali członkowie](obsolete-members.md).

- [Przestarzałe typy w zestawy systemowe](#obsolete_types_in_system_assemblies)

    - [mscorlib.dll](#mscorlib)

    - [System.Core.dll](#Core)

    - [System.Data.dll](#data)

    - [System.Data.OracleClient.dll](#oracleclient)

    - [System.Design.dll](#design)

    - [System.dll](#system)

    - [System.EnterpriseServices.dll](#enterpriseservices)

    - [System.Net.dll](#net)

    - [System.ServiceModel.dll](#servicemodel)

    - [System.Web.dll](#web)

    - [System.Web.Mobile.dll](#mobile)

    - [System.Workflow.Activities.dll](#workflow_activities)

    - [System.Workflow.ComponentModel.dll](#workflow_componentmodel)

    - [System.Workflow.Runtime.dll](#workflow_runtime)

    - [System.WorkflowServices.dll](#workflowservices)

    - [System.Xaml.dll](#xaml)

    - [System.Xml.dll](#xml)

    - [WindowsBase.dll](#WindowsBase)

- [Przestarzałe typy w zestawach firmy Microsoft](#obsolete_types_in_microsoft_assemblies)

    - [IEHost.dll i IEExec.exe](#IEHost)

    - [Microsoft.Build.Engine.dll](#Engine)

    - [Microsoft.JScript.dll](#jscript)

    - [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)

    - [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)

    - [Microsoft.VisualC.dll](#visualc)

<a name="obsolete_types_in_system_assemblies"></a>
## <a name="obsolete-types-in-system-assemblies"></a>Przestarzałe typy w zestawy systemowe
 W poniższej tabeli wymieniono typy, które zostały zadeklarowane jako przestarzałe w zestawy systemowe. Te zestawy są używane dla ogólnych\-cel tworzenia aplikacji, który jest przeznaczony dla .NET Framework.

<a name="mscorlib"></a>
### <a name="assembly-mscorlibdll"></a>Assembly: mscorlib.dll

|Typ|Message|
|----------|-------------|
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Ten typ wskazany wcześniej Wystąpił nieokreślony błąd krytyczny w środowisku uruchomieniowym. Środowisko uruchomieniowe nie jest już zgłasza ten wyjątek, więc ten typ jest przestarzały.|
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Użyj <xref:System.StringComparer?displayProperty=nameWithType> zamiast tego.|
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Użyj <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType> zamiast tego.|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash> Klasy jest przestarzała.|
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5. Użyj <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> klasy w przestrzeni nazw System.Runtime.CompilerServices zamiast tego.|
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|Innego interfejsu API jest dostępna: Emituj <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> zamiast tego atrybutu niestandardowego.|
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Ten atrybut jest przestarzały i zostanie usunięta w przyszłej wersji.|
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> Jest przestarzała.|
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Ten atrybut jest przestarzała. Domeny aplikacji nie są już zgodne kontekst aktywacji granic w wywołaniach interfejsu IDispatch.|
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=nameWithType>.|
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope> jest używana tylko dla zgodności przezroczystości .NET 2.0.|
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute> jest używana tylko dla zgodności przezroczystości .NET 2.0. Użyj <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType> zamiast tego.|
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Ten typ jest przestarzały i zostanie usunięta w przyszłej wersji programu .NET Framework.|
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|Zabezpieczenia deklaratywne na poziomie zestawu jest przestarzała i nie jest już domyślnie jest wymuszany przez środowisko CLR.|
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Ten typ jest przestarzały i zostanie usunięta w przyszłej wersji programu .NET Framework.|

 [Powrót do początku](#introduction)

<a name="Core"></a>
### <a name="assembly-systemcoredll"></a>Zestaw: System.Core.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|Użycie tego typu generuje błąd kompilatora.<br /><br /> Nie należy używać tego typu.|

 [Powrót do początku](#introduction)

<a name="data"></a>
### <a name="assembly-systemdatadll"></a>Zestaw: System.Data.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute> jest przestarzała.|
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes> jest przestarzała.|
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|<xref:System.Data.TypedDataSetGenerator> Klasy zostanie usunięta w przyszłej wersji. Użyj <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> w System.Design.dll.|
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|<xref:System.Xml.XmlDataDocument> Klasy zostanie usunięta w przyszłej wersji.|

 [Powrót do początku](#introduction)

<a name="oracleclient"></a>
### <a name="assembly-systemdataoracleclientdll"></a>Zestaw: System.Data.OracleClient.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory> jest przestarzała.|
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand> jest przestarzała.|
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder> jest przestarzała.|
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection> jest przestarzała.|
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> jest przestarzała.|
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter> jest przestarzała.|
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission> jest przestarzała.|
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType> jest przestarzała.|

 [Powrót do początku](#introduction)

<a name="design"></a>
### <a name="assembly-systemdesigndll"></a>Zestaw: System.Design.dll

|Typ|Message|
|----------|-------------|
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Ta klasa jest przestarzała. Zamiast nich należy używać słów kluczowych <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ Edycja powiązania danych jest uruchamiany za pośrednictwem <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> zamiast siatki właściwości.|
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ Edycja powiązania danych jest uruchamiany za pośrednictwem <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> zamiast siatki właściwości.|
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> i <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> i <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ edycję szablonu jest obsługiwana w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Do obsługi edycji szablonu, udostępnianie danych szablonu w <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> właściwości i wywołania <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsReferenceManager> Zawiera dodatkowe funkcje i umożliwia więcej rozszerzeń. Aby uzyskać <xref:System.Web.UI.Design.WebFormsReferenceManager>, użyj `RootDesigner.ReferenceManager` właściwości z usługi <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsRootDesigner> Zawiera dodatkowe funkcje i umożliwia więcej rozszerzeń. Aby uzyskać <xref:System.Web.UI.Design.WebFormsRootDesigner>, użyj <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> właściwości z usługi <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ edycję szablonu jest obsługiwana w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Do obsługi edycji szablonu, udostępnianie danych szablonu w <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> właściwości i wywołania <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> ponieważ używa ona <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> do edycji zawartości. Regiony projektanta umożliwiają lepsze kontrolowanie różnych zawartości edytowany.|
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ edycję szablonu jest obsługiwana w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Do obsługi edycji szablonu, udostępnianie danych szablonu w <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> właściwości i wywołania <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ edycję szablonu jest obsługiwana w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Do obsługi edycji szablonu, udostępnianie danych szablonu w <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> właściwości i wywołania <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ autoformat — okno dialogowe jest uruchamiany przez projektanta hosta. Lista dostępnych autoformaty jest uwidaczniany w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> w <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> właściwości.|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType> ponieważ używa ona <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> do edycji zawartości. Regiony projektanta umożliwiają lepsze kontrolowanie różnych zawartości edytowany.|

 [Powrót do początku](#introduction)

<a name="system"></a>
### <a name="assembly-systemdll"></a>Zestaw: PLik System.dll

|Typ|Message|
|----------|-------------|
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Ten interfejs jest przestarzała. Dodaj <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> do obsługi typu <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> zamiast tego.|
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Użyj <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> zamiast tego chcesz pracować z nowym modelem ustawienia.|
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Ten atrybut jest przestarzała. Zamiast nich należy używać słów kluczowych <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType>.|
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Ta klasa jest przestarzała.|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Ta klasa jest przestarzała. Używanie liczników wydajności za pośrednictwem <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> klasy zamiast tego.|
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> zamiast niego dostęp i ustawanie globalnego domyślny serwer proxy. Użyj "null" zamiast <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>.|
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|

 [Powrót do początku](#introduction)

<a name="enterpriseservices"></a>
### <a name="assembly-systementerpriseservicesdll"></a>Zestaw: System.EnterpriseServices.dll

|Typ|Message|
|----------|-------------|
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|<xref:System.EnterpriseServices.RegistrationHelperTx> Klasy jest przestarzała.|

 [Powrót do początku](#introduction)

<a name="net"></a>
### <a name="assembly-systemnetdll"></a>Zestaw: System.Net.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|

 [Powrót do początku](#introduction)

<a name="servicemodel"></a>
### <a name="assembly-systemservicemodeldll"></a>Zestaw: System.ServiceModel.dll

|Typ|Message|
|----------|-------------|
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Ten typ jest przestarzały. Aby włączyć protokół Http <xref:System.Net.CookieContainer>, użyj `AllowCookies` właściwości na powiązanie protokołu Http lub <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.|
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|

 [Powrót do początku](#introduction)

<a name="web"></a>
### <a name="assembly-systemwebdll"></a>Zestaw: System.Web.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona przez [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona przez [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona przez [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona przez [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona przez [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Ten typ jest przestarzały. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona przez [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Convert?displayProperty=nameWithType> i <xref:System.String.Format%2A?displayProperty=nameWithType>.|

 [Powrót do początku](#introduction)

<a name="mobile"></a>
### <a name="assembly-systemwebmobiledll"></a>Zestaw: System.Web.Mobile.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i nie powinna być używana. Aby uzyskać informacje o sposobie tworzenia aplikacji dla urządzeń przenośnych ASP.NET, zobacz [platformy ASP.NET dla deweloperów przenośne](https://go.microsoft.com/fwlink/?LinkId=157231).|

 [Powrót do początku](#introduction)

<a name="workflow_activities"></a>
### <a name="assembly-systemworkflowactivitiesdll"></a>Zestaw: System.Workflow.Activities.dll

|Typ|Message|
|----------|-------------|
|Wszystkie typy w <xref:System.Workflow.Activities?displayProperty=nameWithType> przestrzeni nazw|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|

 [Powrót do początku](#introduction)

<a name="workflow_componentmodel"></a>
### <a name="assembly-systemworkflowcomponentmodeldll"></a>Zestaw: System.Workflow.ComponentModel.dll

|Typ|Message|
|----------|-------------|
|Wszystkie typy w <xref:System.Workflow.ComponentModel> przestrzeni nazw, z wyjątkiem <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> i <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|Wszystkie typy w <xref:System.Workflow.ComponentModel.Compiler> przestrzeni nazw, z wyjątkiem <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> i <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|Wszystkie typy w <xref:System.Workflow.ComponentModel.Design> przestrzeni nazw, z wyjątkiem <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|

 [Powrót do początku](#introduction)

<a name="workflow_runtime"></a>
### <a name="assembly-systemworkflowruntimedll"></a>Zestaw: System.Workflow.Runtime.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Activities.Statements.Interop?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 są przestarzałe. Zamiast tego należy użyć typów Workflow 4.0 z <xref:System.Activities>.\*.|
|<xref:System.Activities.Tracking.InteropTrackingRecord?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 są przestarzałe. Zamiast tego należy użyć typów Workflow 4.0 z <xref:System.Activities>.\*.|
|Wszystkie typy w <xref:System.Workflow.Runtime> przestrzeni nazw|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|Wszystkie typy w <xref:System.Workflow.Runtime.Configuration> przestrzeni nazw|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|Wszystkie typy w <xref:System.Workflow.Runtime.DebugEngine> przestrzeni nazw, z wyjątkiem <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|Wszystkie typy w <xref:System.Workflow.Runtime.Hosting> przestrzeni nazw, z wyjątkiem <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|
|Wszystkie typy w <xref:System.Workflow.Runtime.Tracking> przestrzeni nazw|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|

 [Powrót do początku](#introduction)

<a name="workflowservices"></a>
### <a name="assembly-systemworkflowservicesdll"></a>Zestaw: System.WorkflowServices.dll

|Typ|Message|
|----------|-------------|
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|Wszystkie typy w <xref:System.Workflow.Activities?displayProperty=nameWithType> przestrzeni nazw|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|

 [Powrót do początku](#introduction)

<a name="xaml"></a>
### <a name="assembly-systemxamldll"></a>Zestaw: System.Xaml.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|To nie jest używana przez XAML parser. Zajrzyj <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>.|

 [Powrót do początku](#introduction)

<a name="xml"></a>
### <a name="assembly-systemxmldll"></a>Zestaw: System.Xml.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|Najpierw przestarzałe w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Użyj <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> kompilacji schematu i sprawdzania poprawności.|
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Użyj <xref:System.Xml.XmlReader?displayProperty=nameWithType> utworzone przez <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metody przy użyciu odpowiedniego <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> zamiast tego.|
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|Użycie tego typu generuje błąd kompilatora. Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType> zamiast tego.|

 [Powrót do początku](#introduction)

<a name="WindowsBase"></a>
### <a name="assembly-windowsbasedll"></a>Zestaw: WindowsBase.dll

|Typ|Message|
|----------|-------------|
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType> jest przestarzała. Ten interfejs nie jest już używana.|

 [Powrót do początku](#introduction)

<a name="obsolete_types_in_microsoft_assemblies"></a>
## <a name="obsolete-types-in-microsoft-assemblies"></a>Przestarzałe typy w zestawach firmy Microsoft
 W poniższych sekcjach wymieniono przestarzałe typy w zestawach firmy Microsoft. Te zestawy są zestawy specjalnych, takich jak zestawy, przeznaczonych dla poszczególnych języków (na przykład Microsoft.JScript.dll lub Microsoft.VisualC.dll).

<a name="IEHost"></a>
### <a name="assembly-iehostdll-and-ieexecexe"></a>Zestaw: IEHost.dll i IEExec.exe
 Zestawy IEHost.dll i IEExec.exe zostały usunięte z programu .NET Framework. Wszystkie typy i składowe są przestarzałe i nie są obsługiwane począwszy od programu .NET Framework 4. Zestawy te zostały użyte do hostowania kontrolek formularzy Windows Forms i uruchamiania plików wykonywalnych w programie Internet Explorer. Zalecane alternatywne metody obejmują ClickOnce, aplikacje przeglądarki XAML (XBAP) i Microsoft Silverlight.

 [Powrót do początku](#introduction)

<a name="Engine"></a>
### <a name="assembly-microsoftbuildenginedll"></a>Zestaw: Microsoft.Build.Engine.dll

|Typ|Message|
|----------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> z *Microsoft.Build* zestawu zamiast tego.|
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> z *Microsoft.Build* zestawu zamiast tego.|

 [Powrót do początku](#introduction)

<a name="jscript"></a>
### <a name="assembly-microsoftjscriptdll"></a>Zestaw: Microsoft.JScript.dll

|Typ|Message|
|----------|-------------|
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Ten typ została zakończona w programie Visual Studio 2005; nie ma zastępstwa dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|

 [Powrót do początku](#introduction)

<a name="VBCompat"></a>
### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Zestaw: Microsoft.VisualBasic.Compatibility.dll

Aby uzyskać informacje na temat migracji z programu Visual Basic 6, zobacz [Centrum zasobów programu Visual Basic 6.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-basic-6/visual-basic-6.0-documentation).
  
|Typ|Message|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=nameWithType>|Ta składowa jest przestarzała.|

 [Powrót do początku](#introduction)

<a name="VBCompatData"></a>
### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>Zestaw: Microsoft.VisualBasic.Compatibility.Data.dll

|Typ|Message|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=nameWithType>|Ta składowa jest przestarzała.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=nameWithType>|Ta składowa jest przestarzała.|

 [Powrót do początku](#introduction)

<a name="visualc"></a>
### <a name="assembly-microsoftvisualcdll"></a>Zestaw: Microsoft.VisualC.dll

|Typ|Message|
|----------|-------------|
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest przestarzały zestawu i istnieje tylko w przypadku zapewnienia zgodności.|

## <a name="see-also"></a>Zobacz także

- [Przestarzałe elementy w ułatwieniach dostępu](whats-obsolete.md)
- [Przestarzałe elementy członkowskie](obsolete-members.md)
