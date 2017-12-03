---
title: "Przykład dyspozytora tabeli UriTemplate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d2332e5f23c46454d1a876c3e21c5a575d10bf5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Zobacz też  
 [Tabeli UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [Obiekt UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
