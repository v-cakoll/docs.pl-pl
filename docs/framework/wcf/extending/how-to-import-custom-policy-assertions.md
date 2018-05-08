---
title: 'Instrukcje: Importowanie niestandardowych asercji zasad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: b6155296e264bb3ae90aac2ee6b83797e632962e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-import-custom-policy-assertions"></a>Instrukcje: Importowanie niestandardowych asercji zasad
Potwierdzenia zasad opisano wymagania punktu końcowego usługi.  Aplikacje klienckie można użyć potwierdzeń zasad w metadanych usługi, aby skonfigurować klienta powiązanie lub dostosować kontraktu usługi dla punktu końcowego usługi.  
  
 Niestandardowych asercji zasad są importowane z zastosowaniem <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu i przekazywanie obiektu metadanych systemu lub rejestrując implementacja typu w pliku konfiguracji aplikacji.  Implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu podać konstruktora domyślnego.  
  
### <a name="to-import-custom-policy-assertions"></a>Aby importowanie niestandardowych asercji zasad  
  
1.  Implementowanie <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu klasy. Zobacz poniższe procedury.  
  
2.  Wstaw importera zasad niestandardowych albo przez:  
  
3.  Przy użyciu pliku konfiguracji. Zobacz poniższe procedury.  
  
4.  Korzystanie z pliku konfiguracji z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Zobacz poniższe procedury.  
  
5.  Programowane Wstawianie importera zasad. Zobacz poniższe procedury.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Aby zaimplementować interfejs System.ServiceModel.Description.IPolicyImportExtension w dowolnej klasy  
  
1.  W <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> metody, dla każdego tematu zasad, które planuje się, Znajdź potwierdzeń zasad, które chcesz zaimportować, wywołując metodę odpowiednie (w zależności od zakresu potwierdzenia, które mają) na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> obiekt przekazywany do Metoda. Poniższy przykładowy kod przedstawia sposób użycia <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metodę, aby zlokalizować potwierdzenia zasad niestandardowych i usunąć go z kolekcji w jednym kroku. Metoda usuwania umożliwia lokalizowanie i usuwanie potwierdzenia, nie trzeba wykonać krok 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  Przetwarzają potwierdzeń zasad. Należy pamiętać, że system zasad nie normalizacji zagnieżdżone zasad i `wsp:optional`. Te konstrukcje musi przetworzyć w implementacji rozszerzenia importu zasad.  
  
3.  Wykonaj dostosowanie binding lub kontraktu, który obsługuje możliwości lub wymagania określone przez potwierdzenia zasad. Zwykle potwierdzenia wskazują, czy powiązanie wymaga określoną konfigurację lub element określonego powiązania. Wprowadź poniższe zmiany, uzyskując dostęp do <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> właściwości. Inne potwierdzenia wymagać modyfikacji kontraktu.  Masz dostęp i modyfikować za pomocą kontraktu <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> właściwości.  Pamiętaj, że Twoje importera zasad może pobrać wywołana wiele razy dla tego samego powiązania i kontraktu, ale różnych zasad alternatywnych alternatywne zasady importowania kończy się niepowodzeniem. Kod powinien być odporny na takie zachowanie.  
  
4.  Usuń potwierdzenia zasad niestandardowych z kolekcji potwierdzenia. Jeśli potwierdzenie nie zostanie usunięty Windows Communication Foundation (WCF) założono, że importowanie zasad nie powiodło się i nie importuje powiązanie skojarzone. Jeśli używasz <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metodę, aby zlokalizować potwierdzenia zasad niestandardowych i usunąć go z kolekcji w jednym kroku, nie trzeba wykonać ten krok.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Aby wstawić importera zasad niestandardowych do metadanych systemu przy użyciu pliku konfiguracji  
  
1.  Dodaj typ importera `<extensions>` element wewnątrz [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) w pliku konfiguracji klienta.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2.  W aplikacji klienta za pomocą <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> do rozpoznania metadanych i importer jest wywoływana automatycznie.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Aby wstawić importera zasad niestandardowych systemu metadanych, za pomocą Svcutil.exe  
  
1.  Dodaj typ importera `<extensions>` element wewnątrz [ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) elementu w pliku konfiguracyjnym Svcutil.exe.config. Możesz również Svcutil.exe punktu załadować zarejestrowanego w pliku konfiguracji różnych przy użyciu typów importera zasad `/svcutilConfig` opcji.  
  
2.  Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Aby zaimportować metadane i importer jest wywoływana automatycznie.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Aby wstawić importera zasad niestandardowych do systemu metadanych programowo  
  
1.  Dodaj importera <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> właściwości (na przykład, jeśli używasz <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) przed Importowanie metadanych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>  
 [Rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
