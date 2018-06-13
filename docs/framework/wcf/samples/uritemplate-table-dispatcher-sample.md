---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 9075d779b2ca2360c5ad28c3872c54c64aa200b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506019"
---
# <a name="uritemplate-table-dispatcher-sample"></a>Przykład dyspozytora tabeli UriTemplate
<xref:System.UriTemplateTable> Klasa udostępnia struktury tabeli asocjacyjnej słownika podobne do pracy z zestawem <xref:System.UriTemplate> wystąpień. W tym przykładzie przedstawiono podstawowe aparatu wysyłania utworzony za pomocą `UriTemplateTable`, typowy scenariusz użycia dla `UriTemplateTable` klasy.  
  
 W tym przykładzie przedstawiono następujące kluczowe założenia `UriTemplateTable` klasy:  
  
-   Kojarzenie obiektów delegowanych z `UriTemplates` w `UriTemplateTable`.  
  
-   Przy użyciu <xref:System.UriTemplateTable.MatchSingle%2A> można uzyskać obiektu delegowanego obsługi poprawne dla określonego identyfikatora URI.  
  
-   Wywoływanie delegata obsługi do przetworzenia żądania.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
