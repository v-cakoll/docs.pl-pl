---
title: Atrybuty ustawień aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: 09fb5c26f7ecccd427155836c3864773153dddfa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668954"
---
# <a name="application-settings-attributes"></a>Atrybuty ustawień aplikacji
Architektura ustawień aplikacji zawiera wiele atrybutów, które mogą być stosowane do klasy otoki ustawień aplikacji lub jego poszczególnych właściwości. Te atrybuty są sprawdzane w czasie wykonywania przez infrastrukturę ustawienia aplikacji, często specjalnie Dostawca ustawień, aby dostosować jego funkcjonowania określone potrzeby niestandardowej otoki.  
  
 W poniższej tabeli przedstawiono atrybuty, które można zastosować do klasy otoki ustawień aplikacji i/lub poszczególnych właściwości tej klasy. Zgodnie z definicją, tylko jeden zakres atrybut —**UserScopedSettingAttribute** lub **atrybutu ApplicationScopedSettingAttribute**— muszą być stosowane do każdej właściwości ustawienia.  
  
> [!NOTE]
>  Dostawca ustawień niestandardowych, pochodzące z <xref:System.Configuration.SettingsProvider> klasy, jest wymagana tylko do rozpoznawania następujące trzy atrybuty: **Atrybutu ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**, i **DefaultSettingValueAttribute**.  
  
|Atrybut|Cel|Opis|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Oba|Określa krótką nazwę dostawcy ustawień na potrzeby stanu trwałego.<br /><br /> Jeśli ten atrybut nie zostanie podany, domyślny dostawca <xref:System.Configuration.LocalFileSettingsProvider>, zakłada, że.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Oba|Definiuje właściwość jako ustawienia aplikacji użytkownika o określonym zakresie.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Oba|Definiuje właściwość jako ustawienie aplikacji o zakresie aplikacji.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Właściwość|Określa ciąg, który może być zdeserializowany przez dostawcę wartości ustaloną domyślny dla tej właściwości.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Nie wymaga tego atrybutu i spowoduje przesłonięcie żadnej wartości, dostarczone przez ten atrybut w przypadku wartości jeszcze utrwalone.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Właściwość|Udostępnia opisu testu dla poszczególnych ustawień, używane przede wszystkim przez narzędzia w czasie wykonywania oraz w czasie projektowania.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Class|Udostępnia jawna nazwa grupy ustawień. Jeśli ten atrybut jest nieobecne, <xref:System.Configuration.ApplicationSettingsBase> używa nazwy klasy otoki.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Class|Zawiera grupę ustawień, wykorzystywany głównie w czasie wykonywania i czasu projektowania narzędzi opisu testu.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Oba|Określa zero lub więcej usług zarządzania, które należy przekazać do grupy ustawień lub właściwość. Dostępne usługi są opisane przez <xref:System.Configuration.SettingsManageability> wyliczenia.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Właściwość|Wskazuje, czy to ustawienie należy do specjalnych, wstępnie zdefiniowanych kategorii, takich jak parametry połączenia, sugerujące przetwarzana w specjalny sposób przez dostawcę ustawień. Wstępnie zdefiniowane kategorie dla tego atrybutu są definiowane przez <xref:System.Configuration.SpecialSetting> wyliczenia.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Oba|Określa mechanizm serializacji preferowanych ustawień, grupa lub właściwość. Mechanizm serializacji dostępne są definiowane przez <xref:System.Configuration.SettingsSerializeAs> wyliczenia.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Właściwość|Określa, że dostawca ustawień należy wyłączyć wszystkie funkcje uaktualniania aplikacji dla zaznaczonych właściwości.|  
  
 *Klasa* wskazuje, czy atrybut można stosować tylko do klasy otoki ustawień aplikacji. *Właściwość* wskazuje, czy atrybut może zostać zastosowana tylko właściwości ustawień. *Zarówno* wskazuje, że na tym poziomie można zastosować atrybutu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [Architektura ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
- [Instrukcje: Tworzenie ustawień aplikacji](https://msdn.microsoft.com/library/53b3af80-1c02-4e35-99c6-787663148945)
