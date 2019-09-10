---
title: Konwencje schematu konfiguracji programu WIF
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: 6e13915121884ecb4a0e54344e02d29650f54c6f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851481"
---
# <a name="wif-configuration-schema-conventions"></a>Konwencje schematu konfiguracji programu WIF
W tym temacie omówiono konwencje używane w ramach konfiguracji programu Windows Identity Foundation (WIF) i opisano niektóre typowe funkcje i atrybuty używane w programie [ \<system. IdentityModel](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) [ \< > i sekcje system. identityModel. Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) .  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Środka  
 Wiele elementów konfiguracji WIF ma `mode` atrybut. Ten atrybut zwykle określa, która Klasa jest używana do wykonywania określonej części przetwarzania i które elementy konfiguracji mogą być elementami podrzędnymi bieżącego elementu. Błąd konfiguracji zostanie zgłoszony, jeśli elementy, które są zawarte w pliku konfiguracji, zostaną zignorowane z powodu ustawień trybu.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>Wartości TimeSpan  
 Gdzie <xref:System.TimeSpan> jest używany jako typ atrybutu, <xref:System.TimeSpan.Parse%28System.String%29> Zobacz metodę, aby wyświetlić dozwolony format. Ten format jest zgodny z poniższą specyfikacją.  
  
`[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]`  
  
 Na przykład "30", "30.00:00", "30.00:00:00" All oznacza 30 dni; i "00:05", "00:05:00", "0,00:05:00.00" wszystkie oznaczają 5 minut.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Odwołania do certyfikatów  
 Kilka elementów pobiera odwołania do certyfikatów przy użyciu `<certificateReference>` elementu. W przypadku odwoływania się do certyfikatu dostępne są następujące atrybuty.  
  
|||  
|-|-|  
|`storeLocation`|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wyliczenia: `CurrentUser` lub. `CurrentMachine`|  
|`storeName`|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreName> wyliczenia; najbardziej przydatna dla tego `My` kontekstu to i `TrustedPeople`.|  
|`x509FindType`|Wartość <xref:System.Security.Cryptography.X509Certificates.X509FindType> wyliczenia; najbardziej przydatna dla tego `FindBySubjectName` kontekstu to i `FindByThumbprint`. Aby wyeliminować szansę wystąpienia błędu, zaleca `FindByThumbprint` się użycie tego typu w środowiskach produkcyjnych.|  
|`findValue`|Wartość używana do znajdowania certyfikatu na podstawie `x509FindType` atrybutu. Aby wyeliminować szansę wystąpienia błędu, zaleca `FindByThumbprint` się użycie tego typu w środowiskach produkcyjnych. Gdy `FindByThumbPrint` jest określony, ten atrybut przyjmuje wartość, która jest postać ciągu szesnastkowego odcisku palca certyfikatu, na przykład "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Odwołania do typu niestandardowego  
 Kilka elementów odwołuje się do `type` typów niestandardowych przy użyciu atrybutu. Ten atrybut powinien określać nazwę typu niestandardowego. Aby odwołać się do typu z globalnej pamięci podręcznej zestawów (GAC), należy użyć silnej nazwy. Aby odwołać się do typu z zestawu w pojemniku/katalogu, można użyć prostego odwołania kwalifikowanego do zestawu. Typy zdefiniowane w App_Code/Directory mogą być również przywoływane przez po prostu określenie nazwy typu bez zestawu uprawniającego.  
  
 Typy niestandardowe muszą pochodzić od określonego typu i muszą podawać `public` domyślnego konstruktora (0 argumentów).  
  
## <a name="see-also"></a>Zobacz także

- [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)
- [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
