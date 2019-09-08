---
title: 'Instrukcje: importowanie niestandardowych asercji zasad'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: 4510eac2d9c1b3bb64420b0678b3a47a90887188
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795622"
---
# <a name="how-to-import-custom-policy-assertions"></a>Instrukcje: importowanie niestandardowych asercji zasad
Potwierdzenia zasad opisują możliwości i wymagania punktu końcowego usługi.  Aplikacje klienckie mogą używać potwierdzeń zasad w metadanych usługi, aby skonfigurować powiązanie klienta lub dostosować kontrakt usługi dla punktu końcowego usługi.  
  
 Niestandardowe potwierdzenia zasad są importowane przez implementację <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejsu i przekazanie tego obiektu do systemu metadanych lub przez zarejestrowanie typu implementacji w pliku konfiguracyjnym aplikacji.  Implementacje <xref:System.ServiceModel.Description.IPolicyImportExtension> interfejsu muszą udostępniać Konstruktor bez parametrów.  
  
### <a name="to-import-custom-policy-assertions"></a>Aby zaimportować potwierdzenia zasad niestandardowych  
  
1. Zaimplementuj <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interfejs w klasie. Zapoznaj się z poniższymi procedurami.  
  
2. Wstaw importera zasad niestandardowych przez:  
  
3. Przy użyciu pliku konfiguracji. Zapoznaj się z poniższymi procedurami.  
  
4. Korzystanie z pliku konfiguracji z [narzędziem do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Zapoznaj się z poniższymi procedurami.  
  
5. Programowe Wstawianie importera zasad. Zapoznaj się z poniższymi procedurami.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Aby zaimplementować interfejs System. ServiceModel. Description. IPolicyImportExtension dla dowolnej klasy  
  
1. W przypadku poszczególnych interesujących Cię zasad Znajdź potwierdzenia zasad, które chcesz zaimportować, wywołując odpowiednią metodę (w zależności od wymaganego zakresu potwierdzenia) <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> w obiekcie przekazaną do elementu <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> Method. Poniższy przykład kodu pokazuje, jak za pomocą <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metody zlokalizować potwierdzenie zasad niestandardowych i usunąć je z kolekcji w jednym kroku. Jeśli używasz metody Remove do lokalizowania i usuwania potwierdzenia, nie musisz wykonywać kroku 4.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. Przetwarzanie potwierdzeń zasad. Należy pamiętać, że system zasad nie normalizuje zasad zagnieżdżonych `wsp:optional`i. Należy przetwarzać te konstrukcje w implementacji rozszerzenia importu zasad.  
  
3. Wykonaj dostosowanie do powiązania lub kontraktu, który obsługuje możliwości lub wymagania określone przez potwierdzenie zasad. Zazwyczaj potwierdzenia wskazują, że powiązanie wymaga określonej konfiguracji lub określonego elementu powiązania. Wprowadź te modyfikacje, uzyskując dostęp <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> do właściwości. Inne potwierdzenia wymagają zmodyfikowania kontraktu.  Możesz uzyskać dostęp do kontraktu i zmodyfikować go przy <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> użyciu właściwości.  Należy zauważyć, że importer zasad może być wywoływany wiele razy dla tego samego powiązania i kontraktu, ale różne alternatywy dla zasad, jeśli Importowanie alternatywy zasad zakończy się niepowodzeniem. Kod powinien być odporny na to zachowanie.  
  
4. Usuń potwierdzenie zasad niestandardowych z kolekcji potwierdzenia. Jeśli nie usuniesz Windows Communication Foundation potwierdzenia (WCF), przyjęto założenie, że import zasad nie powiódł się i nie importuje skojarzonego powiązania. Jeśli użyto <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> metody, aby zlokalizować potwierdzenie zasad niestandardowych i usunąć je z kolekcji w jednym kroku, nie musisz wykonywać tego kroku.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Aby wstawić importera zasad niestandardowych do systemu metadanych przy użyciu pliku konfiguracji  
  
1. Dodaj typ importera do `<extensions>` elementu [ \<wewnątrz elementu policyImporters >](../../configure-apps/file-schema/wcf/policyimporters.md) w pliku konfiguracji klienta.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2. W aplikacji klienckiej Użyj <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> , aby rozwiązać metadane, a importer jest wywoływany automatycznie.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Aby wstawić importera zasad niestandardowych do systemu metadanych przy użyciu programu Svcutil. exe  
  
1. Dodaj typ importera do `<extensions>` elementu [ \<wewnątrz elementu policyImporters >](../../configure-apps/file-schema/wcf/policyimporters.md) w pliku konfiguracyjnym Svcutil. exe. config. Możesz również wskazać Svcutil. exe, aby załadować typy importerów zasad zarejestrowane w innym pliku konfiguracji przy użyciu `/svcutilConfig` opcji.  
  
2. Użyj [Narzędzia do przesyłania metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w celu zaimportowania metadanych, a importer jest wywoływany automatycznie.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Aby programowo wstawić importera zasad niestandardowych do systemu metadanych  
  
1. Dodaj importera do <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> właściwości (na przykład jeśli <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>używasz) przed zaimportowaniem metadanych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Rozszerzanie systemu metadanych](extending-the-metadata-system.md)
