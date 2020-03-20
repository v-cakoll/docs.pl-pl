---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: aa4259f8c823bebf38b9689df92c45992cb55723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143684"
---
# <a name="uritemplate-table-dispatcher-sample"></a>Przykład dyspozytora tabeli UriTemplate
Klasa <xref:System.UriTemplateTable> zawiera słownika jak struktury tabeli asocjacyjnych do pracy z zestawem <xref:System.UriTemplate> wystąpień. W tym przykładzie przedstawiono podstawowy `UriTemplateTable`aparat dyspozytorny zbudowany przy użyciu , typowy scenariusz użycia dla `UriTemplateTable` klasy.  
  
 W tym przykładzie przedstawiono następujące `UriTemplateTable` kluczowe pojęcia dla klasy:  
  
- Kojarzenie delegatów `UriTemplates` z `UriTemplateTable`w pliku .  
  
- Za <xref:System.UriTemplateTable.MatchSingle%2A> pomocą w celu uzyskania właściwego pełnomocnika obsługi dla określonego identyfikatora URI.  
  
- Wywoływanie delegata programu obsługi do przetwarzania żądania.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Zobacz też

- [Tabela UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
