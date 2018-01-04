---
title: Konwencje schematu konfiguracji WIF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e327b45ddd260d1a52066b5bf53e7114100ff45c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wif-configuration-schema-conventions"></a>Konwencje schematu konfiguracji WIF
W tym temacie opisano konwencje używanych w całym tematy dotyczące konfiguracji systemu Windows Identity Foundation (WIF) oraz opisano niektóre typowe funkcje i atrybuty stosowane w [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) i [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sekcje.  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Tryby  
 Wiele elementów konfiguracji programu WIF `mode` atrybutu. Ten atrybut kontroluje zwykle, których klasa jest używana do określonej części przetwarzania i elementy konfiguracji, które są dozwolone jako elementy podrzędne bieżącego elementu. Błąd konfiguracji zostanie wygenerowany, jeśli elementy, które znajdują się w pliku konfiguracji są ignorowane z powodu ustawienia trybu.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>Wartości TimeSpan  
 Gdzie <xref:System.TimeSpan> jest używany jako typ atrybutu, zobacz <xref:System.TimeSpan.Parse%28System.String%29> metody, aby zobaczyć dozwolone formatu. Ten format jest zgodny ze specyfikacją następujące.  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 Na przykład "30", "30.00:00", "30.00:00:00" wszystkie oznacza 30 dni; i "00:05", "00: 05:00", "0.00:05:00.00" oznacza wszystkie 5 minut.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Odwołania certyfikatów  
 Odwołania do certyfikatów przy użyciu podjąć kilka elementów `<certificateReference>` elementu. Podczas odwoływania się do certyfikatu, następujące atrybuty są dostępne.  
  
|||  
|-|-|  
|`storeLocation`|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wyliczenie: `CurrentUser` lub `CurrentMachine`.|  
|`storeName`|Wartość <xref:System.Security.Cryptography.X509Certificates.StoreName> wyliczenie; najbardziej przydatne dla tego kontekstu są `My` i `TrustedPeople`.|  
|`x509FindType`|Wartość <xref:System.Security.Cryptography.X509Certificates.X509FindType> wyliczenie; najbardziej przydatne dla tego kontekstu są `FindBySubjectName` i `FindByThumbprint`. Aby wyeliminować ryzyko błędów, zalecane jest `FindByThumbprint` typu można używać w środowiskach produkcyjnych.|  
|`findValue`|Wartość używana do znajdowania certyfikatu, na podstawie `x509FindType` atrybutu. Aby wyeliminować ryzyko błędów, zalecane jest `FindByThumbprint` typu można używać w środowiskach produkcyjnych. Gdy `FindByThumbPrint` jest określony, ten atrybut ma wartość, która jest formularz ciąg szesnastkowy certyfikatu odcisku palca, na przykład "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Odwołania do niestandardowego typu  
 Dokumentacja elementów kilka typów niestandardowych za pomocą `type` atrybutu. Ten atrybut powinien określać nazwę typu niestandardowego. Aby odwołać się do typu z globalnej pamięci podręcznej zestawów (GAC), można użyć silnej nazwy. Aby odwołać się do typu z zestawu w pojemniku / directory, może służyć proste odwołanie kwalifikowaną dla zestawu. Typy definiowane w App_Code / katalogu mogą się też odwoływać linie po prostu określić nazwę typu z nie kwalifikującego zestawu.  
  
 Niestandardowe typy musi pochodzić od typu określonego i użytkownik musi podać `public` domyślnego konstruktora (0 argument).  
  
## <a name="see-also"></a>Zobacz też  
 [\<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [\<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
