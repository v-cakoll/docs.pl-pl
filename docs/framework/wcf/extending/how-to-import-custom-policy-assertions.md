---
title: 'Instrukcje: importowanie niestandardowych asercji zasad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: e27c6ed6508544180d8659717b700e604b0f3d3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073627"
---
# <a name="how-to-import-custom-policy-assertions"></a>Instrukcje: importowanie niestandardowych asercji zasad
Asercji zasad opisano możliwości i wymagania dotyczące punktu końcowego usługi.  Klient aplikacje mogą używać asercji zasad w metadanych usługi, aby skonfigurować klienta powiązanie lub dostosować kontraktu usługi dla punktu końcowego usługi.  
  
 Niestandardowych asercji zasad są importowane przez zaimplementowanie <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu i przekazanie tego obiektu, do systemu metadanych lub przez rejestrowanie wykonania typu w pliku konfiguracyjnym aplikacji.  Implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejs musi dostarczyć konstruktora domyślnego.  
  
### <a name="to-import-custom-policy-assertions"></a>Aby importowanie niestandardowych asercji zasad  
  
1.  Implementowanie <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu w klasie. Zobacz poniższe procedury.  
  
2.  Wstaw importera zasad niestandardowych, albo przez:  
  
3.  Korzystanie z pliku konfiguracji. Zobacz poniższe procedury.  
  
4.  Korzystanie z pliku konfiguracji, za pomocą [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Zobacz poniższe procedury.  
  
5.  Programowe Wstawianie importera zasad. Zobacz poniższe procedury.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Aby zaimplementować interfejs System.ServiceModel.Description.IPolicyImportExtension na dowolnej klasy  
  
1.  W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metody dla każdego tematu zasad, który Cię interesuje, Znajdź asercji zasad, które chcesz zaimportować przez wywołanie odpowiedniej metody (w zależności od zakresu asercja, która ma) na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> obiekt przekazany do Metoda. Poniższy przykład kodu pokazuje sposób użycia <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metodę, aby zlokalizować potwierdzeń niestandardowych zasad i usuń go z kolekcji w jednym kroku. Metoda usuwania jest używana do zlokalizowania i usunięcia potwierdzenia, nie trzeba wykonać krok 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  Przetwarzanie asercji zasad. Należy zauważyć, że system zasad nie normalizacji zagnieżdżone zasad i `wsp:optional`. Musi przetwarzać te konstrukcje w danej implementacji rozszerzenia importu zasad.  
  
3.  Wykonaj dostosowanie do powiązania lub kontraktu, który obsługuje możliwości lub wymagania określone przez potwierdzenie zasad. Zazwyczaj potwierdzenia wskazują, że powiązanie wymaga określonej konfiguracji lub element powiązania określone. Wprowadź te zmiany, uzyskując dostęp do <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> właściwości. Asercji innych wymaga, należy zmodyfikować umowy.  Możesz uzyskać dostęp i modyfikowanie za pomocą kontraktu <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> właściwości.  Należy pamiętać, że importera swoje zasady może zostać wywołana wiele razy dla tego samego powiązania i umowy, ale alternatywy inne zasady, zamiast zasady importowania kończy się niepowodzeniem. Kod powinien być odporny na to zachowanie.  
  
4.  Usuń potwierdzeń niestandardowych zasad z kolekcji potwierdzenia. Jeśli potwierdzenie nie zostanie usunięty Windows Communication Foundation (WCF) zakłada, że importowanie zasad nie powiodło się i nie importuje skojarzone powiązania. Jeśli użyto <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metodę, aby zlokalizować potwierdzeń niestandardowych zasad i usuń go z kolekcji w jednym kroku, nie trzeba wykonać ten krok.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Aby wstawić importera niestandardowych zasad do metadanych systemu przy użyciu pliku konfiguracji  
  
1.  Dodaj typ importera `<extensions>` element wewnątrz [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) elementu w pliku konfiguracji klienta.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2.  W aplikacji klienckiej należy używać <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> rozpoznać metadanych i importera jest wywoływana automatycznie.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Aby wstawić importera niestandardowych zasad do systemu metadanych przy użyciu Svcutil.exe  
  
1.  Dodaj typ importera `<extensions>` element wewnątrz [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) elementu w pliku konfiguracyjnym Svcutil.exe.config. Możesz również Svcutil.exe punktu załadować zarejestrowanego w pliku konfiguracji różnych przy użyciu typów importera zasad `/svcutilConfig` opcji.  
  
2.  Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można zaimportować metadanych i importera jest wywoływana automatycznie.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Aby wstawić importera niestandardowych zasad do systemu metadanych programowe  
  
1.  Dodaj importera <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> właściwości (na przykład, jeśli używasz <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) przed zaimportowaniem metadanych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
