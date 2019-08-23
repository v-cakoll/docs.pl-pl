---
title: Atrybuty ustawień aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: b38ed931cab3a333a56dd027d5843b1c8f00dcb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916676"
---
# <a name="application-settings-attributes"></a>Atrybuty ustawień aplikacji
Architektura ustawień aplikacji zawiera wiele atrybutów, które można zastosować do klasy otoki ustawień aplikacji lub jej poszczególnych właściwości. Te atrybuty są sprawdzane w czasie wykonywania według infrastruktury ustawień aplikacji, często specyficznych dla dostawcy ustawień, aby dostosować jego działanie do określonych potrzeb otoki niestandardowej.  
  
 W poniższej tabeli wymieniono atrybuty, które można zastosować do klasy otoki ustawień aplikacji, poszczególnych właściwości tej klasy lub obu tych atrybutów. Zgodnie z definicją należy zastosować tylko jeden atrybut SCOPE-**UserScopedSettingAttribute** lub **ApplicationScopedSettingAttribute**— dla każdej właściwości ustawień.  
  
> [!NOTE]
> Dostawca ustawień niestandardowych, pochodzący z <xref:System.Configuration.SettingsProvider> klasy, jest wymagany tylko do rozpoznawania następujących trzech atrybutów: **ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**i **DefaultSettingValueAttribute**.  
  
|Atrybut|Cel|Opis|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Oba|Określa krótką nazwę dostawcy ustawień, który ma być używany na potrzeby trwałości.<br /><br /> Jeśli ten atrybut nie zostanie podany, zostanie przyjęty domyślny <xref:System.Configuration.LocalFileSettingsProvider>dostawca.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Oba|Definiuje właściwość jako ustawienie aplikacji należącej do zakresu użytkownika.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Oba|Definiuje właściwość jako ustawienie aplikacji w zakresie aplikacji.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Właściwość|Określa ciąg, który może zostać odszeregowany przez dostawcę w postaci wartości domyślnej dla tej właściwości.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Nie wymaga tego atrybutu i przesłoni wszelkie wartości podane przez ten atrybut, jeśli istnieje już wartość.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Właściwość|Zawiera opisowy test dla poszczególnych ustawień, używany głównie przez narzędzia czasu wykonywania i projektowania.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Class|Zapewnia jawną nazwę grupy ustawień. Jeśli ten atrybut nie jest obecny <xref:System.Configuration.ApplicationSettingsBase> , używa nazwy klasy otoki.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Class|Zawiera opisowy test dla grupy ustawień, używany głównie przez narzędzia czasu wykonywania i projektowania.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Oba|Określa zero lub więcej usług zarządzania, które powinny być dostarczone do grupy ustawień lub właściwości. Dostępne usługi są opisane przez <xref:System.Configuration.SettingsManageability> Wyliczenie.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Właściwość|Wskazuje, że ustawienie należy do specjalnej, wstępnie zdefiniowanej kategorii, takiej jak parametry połączenia, która sugeruje specjalne przetwarzanie przez dostawcę ustawień. Wstępnie zdefiniowane kategorie dla tego atrybutu są definiowane przez <xref:System.Configuration.SpecialSetting> Wyliczenie.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Oba|Określa preferowany mechanizm serializacji dla grupy ustawień lub właściwości. Dostępne mechanizmy serializacji są definiowane przez <xref:System.Configuration.SettingsSerializeAs> Wyliczenie.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Właściwość|Określa, że Dostawca ustawień powinien wyłączyć wszystkie funkcje uaktualniania aplikacji dla oznaczonej właściwości.|  
  
 *Klasa* wskazuje, że atrybut może być stosowany tylko do klasy otoki ustawień aplikacji. *Właściwość* wskazuje, że atrybut może być stosowany tylko do właściwości ustawień. *Oba* te elementy wskazują, że atrybut może być stosowany na dowolnym poziomie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [Architektura ustawień aplikacji](application-settings-architecture.md)
- [Instrukcje: Utwórz ustawienia aplikacji](how-to-create-application-settings.md)
