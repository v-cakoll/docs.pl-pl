---
title: Przestarzałe typy w programie .NET Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f30b9e245ad38b0e861590e9b2ca3658a2b5e967
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="obsolete-types-in-the-net-framework"></a>Przestarzałe typy w programie .NET Framework
<a name="introduction"></a> W tabelach w tym artykule przedstawiono typy, które są nieaktualne w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], uporządkowany według zestawu. Użyj następujących łączy, aby wyświetlić listę przestarzałe typy i zalecanych rozwiązań alternatywnych w każdym zestawie. Ponieważ te typy są nieaktualne, ich elementy Członkowskie również są nieaktualne. Aby uzyskać listę dodatkowych przestarzali członkowie w bibliotece klas programu .NET Framework, zobacz [Przestarzali członkowie](../../../docs/framework/whats-new/obsolete-members.md).  
  
-   [Przestarzałe typy w zestawach systemu](#obsolete_types_in_system_assemblies)  
  
    -   [mscorlib.dll](#mscorlib)  
  
    -   [System.Core.dll](#Core)  
  
    -   [System.Data.dll](#data)  
  
    -   [System.Data.OracleClient.dll](#oracleclient)  
  
    -   [System.Design.dll](#design)  
  
    -   [System.dll](#system)  
  
    -   [System.EnterpriseServices.dll](#enterpriseservices)  
  
    -   [System.Net.dll](#net)  
  
    -   [System.ServiceModel.dll](#servicemodel)  
  
    -   [System.Web.dll](#web)  
  
    -   [System.Web.Mobile.dll](#mobile)  
  
    -   [System.Workflow.Activities.dll](#workflow_activities)  
  
    -   [System.Workflow.ComponentModel.dll](#workflow_componentmodel)  
  
    -   [System.Workflow.Runtime.dll](#workflow_runtime)  
  
    -   [System.WorkflowServices.dll](#workflowservices)  
  
    -   [System.Xaml.dll](#xaml)  
  
    -   [System.Xml.dll](#xml)  
  
    -   [WindowsBase.dll](#WindowsBase)  
  
-   [Przestarzałe typy w zestawach firmy Microsoft](#obsolete_types_in_microsoft_assemblies)  
  
    -   [IEHost.dll i IEExec.exe](#IEHost)  
  
    -   [Microsoft.Build.Engine.dll](#Engine)  
  
    -   [Microsoft.JScript.dll](#jscript)  
  
    -   [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)  
  
    -   [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)  
  
    -   [Microsoft.VisualC.dll](#visualc)  
  
<a name="obsolete_types_in_system_assemblies"></a>   
## <a name="obsolete-types-in-system-assemblies"></a>Przestarzałe typy w zestawach systemu  
 W poniższych tabelach przedstawiono typy, które zostały zgłoszone przestarzałe w zestawach systemu. Te zestawy są używane w przypadku ogólnych\-celu projektowania aplikacji, przeznaczonego dla programu .NET Framework.  
  
<a name="mscorlib"></a>   
### <a name="assembly-mscorlibdll"></a>Zestaw: mscorlib.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Ten typ wskazanej wcześniej Wystąpił nieokreślony błąd krytyczny w czasie wykonywania. Środowisko uruchomieniowe nie generuje już tego wyjątku, ten typ jest przestarzałe.|  
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Użyj <xref:System.StringComparer?displayProperty=nameWithType> zamiast tego.|  
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Użyj <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType> zamiast tego.|  
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash> Klasy jest przestarzała.|  
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5. Użyj <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> klas w przestrzeni nazw System.Runtime.CompilerServices zamiast tego.|  
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
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Ten atrybut jest przestarzała i zostanie usunięta w przyszłych wersjach.|  
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> Jest przestarzały.|  
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType>.|  
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType>.|  
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType>.|  
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType>.|  
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType>.|  
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType>.|  
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType>.|  
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Ten atrybut jest przestarzała. Domeny aplikacji nie jest już zgodne granice kontekst aktywacji w wywołaniach interfejsu IDispatch.|  
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
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope> jest używana tylko dla zgodności przezroczystość .NET 2.0.|  
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute> jest używana tylko dla zgodności przezroczystość .NET 2.0. Użyj <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType> zamiast tego.|  
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Ten typ jest przestarzałe i zostanie usunięta w przyszłej wersji programu .NET Framework.|  
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|Zabezpieczenia deklaracyjne poziomu zestawu jest przestarzały i nie jest wymuszana przez środowisko CLR domyślnie.|  
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Ten typ jest przestarzałe i zostanie usunięta w przyszłej wersji programu .NET Framework.|  
  
 [Powrót do początku](#introduction)  
  
<a name="Core"></a>   
### <a name="assembly-systemcoredll"></a>Assembly: System.Core.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|Użycie tego typu generuje błąd kompilatora.<br /><br /> Nie należy używać tego typu.|  
  
 [Powrót do początku](#introduction)  
  
<a name="data"></a>   
### <a name="assembly-systemdatadll"></a>Assembly: System.Data.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute> jest przestarzała.|  
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes> jest przestarzała.|  
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|<xref:System.Data.TypedDataSetGenerator> Klasa zostanie usunięta w przyszłej wersji. Użyj <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> w System.Design.dll.|  
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|<xref:System.Xml.XmlDataDocument> Klasa zostanie usunięta w przyszłej wersji.|  
  
 [Powrót do początku](#introduction)  
  
<a name="oracleclient"></a>   
### <a name="assembly-systemdataoracleclientdll"></a>Assembly: System.Data.OracleClient.dll  
  
|Typ|Komunikat|  
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
### <a name="assembly-systemdesigndll"></a>Assembly: System.Design.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Ta klasa jest przestarzała. Zamiast nich należy używać słów kluczowych <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ Edycja powiązania danych jest uruchamiana za pomocą <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> zamiast siatki właściwości.|  
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ Edycja powiązania danych jest uruchamiana za pomocą <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> zamiast siatki właściwości.|  
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> i <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> i <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ edytowanie szablonu jest obsługiwane w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Aby umożliwić edytowanie szablonu, ujawniać dane szablonu w <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> właściwości i wywołanie <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsReferenceManager> Zawiera dodatkowe funkcje oraz umożliwia więcej rozszerzeń. Aby uzyskać <xref:System.Web.UI.Design.WebFormsReferenceManager>, użyj `RootDesigner.ReferenceManager` właściwość z Twojego <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsRootDesigner> Zawiera dodatkowe funkcje oraz umożliwia więcej rozszerzeń. Aby uzyskać <xref:System.Web.UI.Design.WebFormsRootDesigner>, użyj <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> właściwość z Twojego <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ edytowanie szablonu jest obsługiwane w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Aby umożliwić edytowanie szablonu, ujawniać dane szablonu w <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> właściwości i wywołanie <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> ponieważ używa <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> do edycji zawartości. Projektanta regionów umożliwia lepszą kontrolę nad zawartością edytowany.|  
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ edytowanie szablonu jest obsługiwane w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Aby umożliwić edytowanie szablonu, ujawniać dane szablonu w <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> właściwości i wywołanie <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ edytowanie szablonu jest obsługiwane w <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Aby umożliwić edytowanie szablonu, ujawniać dane szablonu w <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> właściwości i wywołanie <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ autoformatowania jest uruchamiana przez projektanta hosta. Lista dostępnych autoformaty jest narażony na <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> w <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType> ponieważ używa <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> do edycji zawartości. Projektanta regionów umożliwia lepszą kontrolę nad zawartością edytowany.|  
  
 [Powrót do początku](#introduction)  
  
<a name="system"></a>   
### <a name="assembly-systemdll"></a>Zestaw: System.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Ten interfejs jest przestarzała. Dodaj <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> do obsługi typu <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> zamiast tego.|  
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Użyj <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> zamiast tego do pracy z modelem nowych ustawień.|  
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Ten atrybut jest przestarzała. Zamiast nich należy używać słów kluczowych <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType>. Na przykład, aby określić projektanta głównego dla CodeDom, użyj `DesignerSerializerAttribute\(...,typeof\(TypeCodeDomSerializer\)\)`.|  
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Ta klasa jest przestarzała.|  
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj liczniki wydajności za pośrednictwem <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> zamiast klasy.|  
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> zamiast tego do uzyskania dostępu i ustawienia globalne domyślny serwer proxy. Użyj wartości "null" zamiast <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>.|  
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
  
 [Powrót do początku](#introduction)  
  
<a name="enterpriseservices"></a>   
### <a name="assembly-systementerpriseservicesdll"></a>Assembly: System.EnterpriseServices.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|<xref:System.EnterpriseServices.RegistrationHelperTx> Klasy jest przestarzała.|  
  
 [Powrót do początku](#introduction)  
  
<a name="net"></a>   
### <a name="assembly-systemnetdll"></a>Assembly: System.Net.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
  
 [Powrót do początku](#introduction)  
  
<a name="servicemodel"></a>   
### <a name="assembly-systemservicemodeldll"></a>Assembly: System.ServiceModel.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|  
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Ten typ jest przestarzałe. Aby włączyć protokół Http <xref:System.Net.CookieContainer>, użyj `AllowCookies` właściwości na powiązanie protokołu Http lub <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.|  
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|  
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|  
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|  
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|  
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Funkcja kanał elementu równorzędnego jest przestarzała i zostanie usunięte w przyszłości.|  
  
 [Powrót do początku](#introduction)  
  
<a name="web"></a>   
### <a name="assembly-systemwebdll"></a>Assembly: System.Web.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Ten typ jest przestarzałe. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona [Account firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|  
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|  
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Ten typ jest przestarzałe. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona [Account firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Ten typ jest przestarzałe. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona [Account firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Ten typ jest przestarzałe. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona [Account firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Ten typ jest przestarzałe. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona [Account firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Ten typ jest przestarzałe. Produkt uwierzytelniania usługi Passport nie jest już obsługiwana i została zastąpiona [Account firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=733413)|  
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|Zalecaną alternatywą jest <xref:System.Convert?displayProperty=nameWithType> i <xref:System.String.Format%2A?displayProperty=nameWithType>.|  
  
 [Powrót do początku](#introduction)  
  
<a name="mobile"></a>   
### <a name="assembly-systemwebmobiledll"></a>Assembly: System.Web.Mobile.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|Zestaw System.Web.Mobile.dll jest przestarzała i powinna już używać. Aby uzyskać informacje dotyczące tworzenia aplikacji platformy ASP.NET dla urządzeń przenośnych, zobacz [ASP.NET dla przenośne](http://go.microsoft.com/fwlink/?LinkId=157231).|  
  
 [Powrót do początku](#introduction)  
  
<a name="workflow_activities"></a>   
### <a name="assembly-systemworkflowactivitiesdll"></a>Assembly: System.Workflow.Activities.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|Wszystkie typy w <xref:System.Workflow.Activities?displayProperty=nameWithType> przestrzeni nazw|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
  
 [Powrót do początku](#introduction)  
  
<a name="workflow_componentmodel"></a>   
### <a name="assembly-systemworkflowcomponentmodeldll"></a>Assembly: System.Workflow.ComponentModel.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|Wszystkie typy w <xref:System.Workflow.ComponentModel> przestrzeni nazw poza <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> i <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|Wszystkie typy w <xref:System.Workflow.ComponentModel.Compiler> przestrzeni nazw poza <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> i <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|Wszystkie typy w <xref:System.Workflow.ComponentModel.Design> przestrzeni nazw z wyjątkiem <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
  
 [Powrót do początku](#introduction)  
  
<a name="workflow_runtime"></a>   
### <a name="assembly-systemworkflowruntimedll"></a>Assembly: System.Workflow.Runtime.dll  
  
|Typ|Komunikat|  
|----------|-------------| 
|<xref:System.Activities.Statements.Interop>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 są przestarzałe. Zamiast tego należy użyć typów Workflow 4.0 z <xref:System.Activities>.\*.|  
|<xref:System.Activities.Tracking.InteropTrackingRecord>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 są przestarzałe. Zamiast tego należy użyć typów Workflow 4.0 z <xref:System.Activities>.\*.|   
|Wszystkie typy w <xref:System.Workflow.Runtime> przestrzeni nazw|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|Wszystkie typy w <xref:System.Workflow.Runtime.Configuration> przestrzeni nazw|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|Wszystkie typy w <xref:System.Workflow.Runtime.DebugEngine> przestrzeni nazw z wyjątkiem <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|Wszystkie typy w <xref:System.Workflow.Runtime.Hosting> przestrzeni nazw z wyjątkiem <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
|Wszystkie typy w <xref:System.Workflow.Runtime.Tracking> przestrzeni nazw|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> System.Workflow. \* typy są przestarzałe. Zamiast tego użyj nowych typów z <xref:System.Activities>.\*.|  
  
 [Powrót do początku](#introduction)  
  
<a name="workflowservices"></a>   
### <a name="assembly-systemworkflowservicesdll"></a>Assembly: System.WorkflowServices.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|Wszystkie typy w <xref:System.Workflow.Activities?displayProperty=nameWithType> przestrzeni nazw|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Typy WF 3 są przestarzałe. Zamiast tego użyj nowych typów WF 4 z <xref:System.Activities>.\*.|  
  
 [Powrót do początku](#introduction)  
  
<a name="xaml"></a>   
### <a name="assembly-systemxamldll"></a>Assembly: System.Xaml.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|Ta nie jest używana przez XAML parser. Zapoznaj się <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>.|  
  
 [Powrót do początku](#introduction)  
  
<a name="xml"></a>   
### <a name="assembly-systemxmldll"></a>Assembly: System.Xml.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|Najpierw jest przestarzała w programie .NET Framework 4.5.<br /><br /> Użycie tego typu generuje błąd kompilatora.<br /><br /> Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Użyj <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> Kompilacja schematu i sprawdzania poprawności.|  
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Użyj <xref:System.Xml.XmlReader?displayProperty=nameWithType> utworzone przez <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metodę przy użyciu odpowiednich <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> zamiast tego.|  
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|Użycie tego typu generuje błąd kompilatora. Ten interfejs API obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie.|  
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType> zamiast tego.|  
  
 [Powrót do początku](#introduction)  
  
<a name="WindowsBase"></a>   
### <a name="assembly-windowsbasedll"></a>Zestaw: WindowsBase.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType> jest przestarzała. Ten interfejs nie jest już używana.|  
  
 [Powrót do początku](#introduction)  
  
<a name="obsolete_types_in_microsoft_assemblies"></a>   
## <a name="obsolete-types-in-microsoft-assemblies"></a>Przestarzałe typy w zestawach firmy Microsoft  
 W poniższych sekcjach wymieniono przestarzałe typy w zestawach firmy Microsoft. Te zestawy są zestawy specjalnych, takich jak zestawy, które odnoszą się do konkretnego języka (na przykład Microsoft.JScript.dll lub Microsoft.VisualC.dll).  
  
<a name="IEHost"></a>   
### <a name="assembly-iehostdll-and-ieexecexe"></a>Zestawu: IEHost.dll i IEExec.exe  
 Zestawy IEHost.dll i IEExec.exe zostały usunięte z programu .NET Framework. Wszystkie typy i ich elementy członkowskie są przestarzałe i nie są obsługiwane w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Te zestawy były używane do hostowania formantów formularzy systemu Windows, a także aby uruchamiać pliki wykonywalne w programie Internet Explorer. Zalecane alternatywne metody obejmują ClickOnce, aplikacje przeglądarki XAML (XBAP) i Microsoft Silverlight.  
  
 [Powrót do początku](#introduction)  
  
<a name="Engine"></a>   
### <a name="assembly-microsoftbuildenginedll"></a>Assembly: Microsoft.Build.Engine.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> z *Microsoft.Build* zestawu zamiast tego.|  
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Ta klasa jest przestarzała. Użyj <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> z *Microsoft.Build* zestawu zamiast tego.|  
  
 [Powrót do początku](#introduction)  
  
<a name="jscript"></a>   
### <a name="assembly-microsoftjscriptdll"></a>Assembly: Microsoft.JScript.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Użycie tego typu nie jest zalecane, ponieważ jest on przestarzały w programie Visual Studio 2005; nie będzie żadnych zastąpienia dla tej funkcji. Zobacz <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentacji, aby uzyskać dodatkową pomoc.|  
  
 [Powrót do początku](#introduction)  
  
<a name="VBCompat"></a>   
### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Assembly: Microsoft.VisualBasic.Compatibility.dll  
  Aby uzyskać informacje na temat migracji z programu Visual Basic 6, zobacz [Visual Basic 6.0 Resource Center](https://msdn.microsoft.com/library/windows/desktop/ms788229).
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
### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>Assembly: Microsoft.VisualBasic.Compatibility.Data.dll  
  
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
### <a name="assembly-microsoftvisualcdll"></a>Zestaw: Microsoft.VisualC.dll  
  
|Typ|Komunikat|  
|----------|-------------|  
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll jest zestawem przestarzałe i istnieje tylko w przypadku zapewnienia zgodności.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe elementy w ułatwieniach dostępu](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Przestarzałe elementy członkowskie](../../../docs/framework/whats-new/obsolete-members.md)
