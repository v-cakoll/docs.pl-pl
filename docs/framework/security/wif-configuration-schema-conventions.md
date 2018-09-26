---
title: Konwencje schematu konfiguracji programu WIF
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: dc2e8f7070af3ef907e4987964bb5aa83f889186
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070360"
---
# <a name="wif-configuration-schema-conventions"></a>Konwencje schematu konfiguracji programu WIF
W tym temacie omówiono Konwencji używanych w całym tematy dotyczące konfigurowania Windows Identity Foundation (WIF) i opisano niektóre typowe funkcje i atrybuty są używane w [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) i [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sekcje.  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Tryby  
 Wiele elementów konfiguracji programu WIF ma `mode` atrybutu. Ten atrybut zwykle kontroluje, która klasa jest używana w celu określoną część przetwarzania i elementy konfiguracji, które są dozwolone jako elementy podrzędne bieżącego elementu. Błąd konfiguracji zostanie wygenerowany, jeśli elementy, które znajdują się w pliku konfiguracji są ignorowane z powodu ustawienia trybu.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>Wartości TimeSpan  
 Gdzie <xref:System.TimeSpan> jest używany jako typ atrybutu, zobacz <xref:System.TimeSpan.Parse%28System.String%29> metodę, aby zobaczyć dozwolonym formatem. Ten format jest zgodny ze specyfikacją następujące.  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 Na przykład "30", "30.00:00", "30.00:00:00" wszystkie oznacza 30 dni i "00:05", "00: 05:00", "0.00:05:00.00" oznacza wszystkie 5 minut.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Odwołania do certyfikatu  
 Niektóre elementy zająć odwołań do certyfikatów przy użyciu `<certificateReference>` elementu. Podczas odwoływania się do certyfikatu, dostępne są następujące atrybuty.  
  
|||  
|-|-|  
|`storeLocation`|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wyliczenia: `CurrentUser` lub `CurrentMachine`.|  
|`storeName`|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreName> wyliczenie; najbardziej przydatne dla tego kontekstu jest `My` i `TrustedPeople`.|  
|`x509FindType`|Wartość <xref:System.Security.Cryptography.X509Certificates.X509FindType> wyliczenie; najbardziej przydatne dla tego kontekstu jest `FindBySubjectName` i `FindByThumbprint`. Aby wyeliminować ryzyko błędów, zalecane jest `FindByThumbprint` typu można używać w środowiskach produkcyjnych.|  
|`findValue`|Wartość używana do znajdowania certyfikatu, na podstawie `x509FindType` atrybutu. Aby wyeliminować ryzyko błędów, zalecane jest `FindByThumbprint` typu można używać w środowiskach produkcyjnych. Gdy `FindByThumbPrint` jest określony, ten atrybut ma wartość, która jest to forma szesnastkowe string certyfikatu odciskiem palca, na przykład "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Odwołania do niestandardowego typu  
 Niektóre elementy odwoływać się do typów niestandardowych przy użyciu `type` atrybutu. Ten atrybut należy określić nazwę typu niestandardowego. Aby odwołać się do typu z globalnej pamięci podręcznej zestawów (GAC), należy używać silnej nazwy. Aby odwołać się do typu z zestawu w pojemniku / katalog, mogą być używane proste odwołanie kwalifikowanych dla zestawu. Typy definiowane w App_Code / katalogu może się też odwoływać po prostu określić nazwę typu z żadnego zestawu kwalifikacji.  
  
 Niestandardowe typy musi pochodzić od typu określonego i muszą one `public` domyślnego konstruktora (0 argument).  
  
## <a name="see-also"></a>Zobacz też  
 [\<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [\<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
