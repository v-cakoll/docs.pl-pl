---
title: Przykład dyspozytora tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 97e916aaf9d137eb7931470f9565797b03620d28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591075"
---
# <a name="uritemplate-table-dispatcher-sample"></a>Przykład dyspozytora tabeli UriTemplate
<xref:System.UriTemplateTable>Klasa zawiera strukturę tabeli asocjacyjnej, która umożliwia pracę z zestawem <xref:System.UriTemplate> wystąpień. W tym przykładzie przedstawiono podstawowy aparat wysyłania, który został utworzony przy użyciu `UriTemplateTable` , typowy scenariusz użycia dla `UriTemplateTable` klasy.  
  
 Ten przykład ilustruje następujące kluczowe pojęcia dotyczące `UriTemplateTable` klasy:  
  
- Kojarzenie delegatów za pomocą `UriTemplates` elementu w `UriTemplateTable` .  
  
- Korzystanie <xref:System.UriTemplateTable.MatchSingle%2A> z programu w celu uzyskania poprawnego delegata programu obsługi dla określonego identyfikatora URI.  
  
- Wywoływanie delegata procedury obsługi w celu przetworzenia żądania.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
2. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Zobacz też

- [Tabela UriTemplate](uritemplate-table-sample.md)
- [UriTemplate](uritemplate-sample.md)
