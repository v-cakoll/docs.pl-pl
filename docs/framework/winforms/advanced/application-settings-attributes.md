---
title: "Atrybuty ustawień aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4255356d4e50f3e8be28024f29701e0e9c010473
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-attributes"></a>Atrybuty ustawień aplikacji
Architektura ustawień aplikacji zawiera wiele atrybutów, które można zastosować do klasy otoki ustawień aplikacji lub jego poszczególnych właściwości. Te atrybuty są badane w czasie wykonywania przez infrastrukturę ustawienia aplikacji, często w szczególności dostawcy ustawień, aby dostosować działanie do określonych potrzeb otoki niestandardowe.  
  
 W poniższej tabeli przedstawiono atrybuty, które można zastosować do klasy otoki ustawień aplikacji i poszczególnych właściwości tej klasy. Zgodnie z definicją tylko atrybut pojedynczy zakres —**UserScopedSettingAttribute** lub **atrybutu ApplicationScopedSettingAttribute**— należy zastosować do poszczególnych ustawień właściwości.  
  
> [!NOTE]
>  Dostawca ustawień niestandardowych, pochodzących z <xref:System.Configuration.SettingsProvider> klasa, jest wymagana tylko do rozpoznawania trzy następujące atrybuty: **atrybutu ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**, i **DefaultSettingValueAttribute**.  
  
|Atrybut|docelowy|Opis|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Zarówno|Określa krótką nazwę dostawcy ustawień na potrzeby trwałości.<br /><br /> Jeśli ten atrybut nie zostanie podany, domyślny dostawca <xref:System.Configuration.LocalFileSettingsProvider>, zakłada, że.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Zarówno|Definiuje właściwość jako ustawienie aplikacji o zakresie użytkownika.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Zarówno|Definiuje właściwość jako ustawienie aplikacji o zakresie aplikacji.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Właściwość|Określa ciąg, który może być zdeserializowany przez dostawcę na wartość domyślną ustalony dla tej właściwości.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Nie wymaga tego atrybutu, a następnie spowoduje zastąpienie wartości podane przez ten atrybut, jeśli istnieje wartość jeszcze utrwalone.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Właściwość|Zawiera opis testu indywidualnego ustawienia używana głównie przez narzędzia środowiska wykonawczego i w czasie projektowania.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Class|Udostępnia jawna nazwa grupy ustawień. W przypadku braku tego atrybutu <xref:System.Configuration.ApplicationSettingsBase> używa nazwy klasy otoki.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Class|Zawiera opis testu dla grupy ustawień, używana głównie przez narzędzia środowiska wykonawczego i w czasie projektowania.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Zarówno|Określa zero lub więcej usług zarządzania, które powinny zostać dostarczone do ustawienia Grupa lub właściwość. Opisano dostępne usługi przez <xref:System.Configuration.SettingsManageability> wyliczenia.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Właściwość|Wskazuje, że jest to ustawienie należy do specjalnej, wstępnie zdefiniowanych kategorii, takiego jak ciąg połączenia, które sugeruje specjalnego przetwarzania przez dostawcę ustawień. Wstępnie zdefiniowanych kategorii dla tego atrybutu są definiowane przez <xref:System.Configuration.SpecialSetting> wyliczenia.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Zarówno|Określa mechanizm serializacji preferowanych ustawień grupa lub właściwość. Mechanizmy serializacji dostępne są definiowane przez <xref:System.Configuration.SettingsSerializeAs> wyliczenia.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Właściwość|Określa, czy dostawca ustawień należy wyłączyć wszystkie funkcje uaktualniania aplikacji dla zaznaczonych właściwości.|  
  
 *Klasa* wskazuje, czy atrybut można stosować tylko do klasy otoki ustawienia aplikacji. *Właściwość* wskazuje, czy atrybut może być stosowane tylko właściwości ustawień. *Zarówno* wskazuje, że ten atrybut można zastosować na tym poziomie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 [Architektura ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Instrukcje: tworzenie ustawień aplikacji](http://msdn.microsoft.com/en-us/53b3af80-1c02-4e35-99c6-787663148945)
