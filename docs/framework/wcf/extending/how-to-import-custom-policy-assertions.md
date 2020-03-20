---
title: 'Instrukcje: Importowanie niestandardowych asercji zasad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: ed8aae30875e3b17f65be5857c7d93af98db9b3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185556"
---
# <a name="how-to-import-custom-policy-assertions"></a>Instrukcje: Importowanie niestandardowych asercji zasad
Potwierdzenia zasad opisują możliwości i wymagania punktu końcowego usługi.  Aplikacje klienckie mogą używać potwierdzeń zasad w metadanych usługi, aby skonfigurować powiązanie klienta lub dostosować umowę serwisową dla punktu końcowego usługi.  
  
 Potwierdzenia zasad niestandardowych są importowane <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> przez implementację interfejsu i przekazywanie tego obiektu do systemu metadanych lub przez zarejestrowanie typu implementacji w pliku konfiguracji aplikacji.  Implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu musi zapewnić konstruktora bez parametrów.  
  
### <a name="to-import-custom-policy-assertions"></a>Aby zaimportować potwierdzenia zasad niestandardowych  
  
1. Zaimplementuj <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejs w klasie. Zobacz następujące procedury.  
  
2. Wstaw importera niestandardowych zasad przez:  
  
3. Korzystanie z pliku konfiguracyjnego. Zobacz następujące procedury.  
  
4. Korzystanie z pliku konfiguracyjnego za pomocą [narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Zobacz następujące procedury.  
  
5. Programowo wstawianie importera polityki. Zobacz następujące procedury.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Aby zaimplementować interfejs System.ServiceModel.Description.IPolicyImportEkstywacja na dowolnej klasie  
  
1. W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metodzie dla każdego tematu zasad, który cię interesuje, znajdź potwierdzenia zasad, które chcesz zaimportować, wywołując odpowiednią <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> metodę (w zależności od zakresu potwierdzenia, który chcesz) na obiekt przeszedł do metody. Poniższy przykład kodu pokazuje, <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> jak użyć metody, aby zlokalizować potwierdzenia zasad niestandardowych i usunąć go z kolekcji w jednym kroku. Jeśli używasz metody usuwania, aby zlokalizować i usunąć twierdzenie, nie trzeba wykonywać krok 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. Przetwórz potwierdzenia zasad. Należy zauważyć, że system zasad nie `wsp:optional`normalizuje zasad zagnieżdżonych i . Należy przetworzyć te konstrukcje w implementacji rozszerzenia importu zasad.  
  
3. Wykonaj dostosowanie do powiązania lub umowy, która obsługuje możliwości lub wymagania określone przez asercja zasad. Zazwyczaj potwierdzenia wskazują, że powiązanie wymaga określonej konfiguracji lub określonego elementu wiązania. Wykonuj te <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> modyfikacje, uzyskując dostęp do właściwości. Inne twierdzenia wymagają, aby zmodyfikować umowy.  Można uzyskać dostęp i zmodyfikować umowę za pomocą <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> właściwości.  Należy zauważyć, że importer zasad może być wywoływany wiele razy dla tego samego powiązania i umowy, ale różne alternatywy zasad, jeśli importowanie alternatywy zasad nie powiedzie się. Kod powinien być odporny na to zachowanie.  
  
4. Usuń potwierdzenia zasad niestandardowych z kolekcji asercji. Jeśli nie usuniesz potwierdzenia Windows Communication Foundation (WCF) zakłada, że importowanie zasad nie powiodło się i nie importuje skojarzonego powiązania. Jeśli użyto <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metody, aby zlokalizować potwierdzenia zasad niestandardowych i usunąć go z kolekcji w jednym kroku nie trzeba wykonać ten krok.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Aby wstawić importera zasad niestandardowych do systemu metadanych przy użyciu pliku konfiguracyjnego  
  
1. Dodaj typ importera `<extensions>` do elementu wewnątrz [ \<policyImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) element w pliku konfiguracji klienta.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]
  
2. W aplikacji klienckiej <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> użyj lub rozwiązać metadane i importer jest wywoływany automatycznie.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Aby wstawić importera niestandardowych zasad do systemu metadanych przy użyciu pliku Svcutil.exe  
  
1. Dodaj typ importera `<extensions>` do elementu wewnątrz [ \<policyImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) element w pliku konfiguracyjnym Svcutil.exe.config. Można również wskazać program Svcutil.exe, aby załadować typy `/svcutilConfig` importerów zasad zarejestrowane w innym pliku konfiguracyjnym przy użyciu tej opcji.  
  
2. Użyj [narzędzia narzędzia servicemodel metadata Utility Tool (Svcutil.exe),](../servicemodel-metadata-utility-tool-svcutil-exe.md) aby zaimportować metadane, a importer jest wywoływany automatycznie.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Aby programowo wstawić importera niestandardowych zasad do systemu metadanych  
  
1. Dodaj importera <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> do właściwości (na przykład, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>jeśli używasz ) przed zaimportowanie metadanych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Rozszerzanie systemu metadanych](extending-the-metadata-system.md)
