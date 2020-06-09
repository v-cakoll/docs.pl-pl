---
title: Przykład elementu UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: fb956882ae653f584026fefb20e261c90010ca9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591062"
---
# <a name="uritemplate-sample"></a>Przykład elementu UriTemplate
<xref:System.UriTemplate>Klasa zawiera metody pracy z zestawami identyfikatorów URI, które mają wspólną strukturę. Ten przykład ilustruje następujące kluczowe pojęcia dotyczące `UriTemplate` :  
  
- Składnia służąca do tworzenia szablonów.  
  
- Tworzenie wystąpienia identyfikatorów URI z `UriTemplate` użyciem <xref:System.UriTemplate.BindByName%2A> i <xref:System.UriTemplate.BindByPosition%2A> .  
  
- <xref:System.UriTemplateTable.Match%2A>, która jest operacją odwrotną `BindByName` i `BindByPosition` .  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a>Zobacz też

- [Tabela UriTemplate](uritemplate-table-sample.md)
- [Dyspozytor tabeli UriTemplate](uritemplate-table-dispatcher-sample.md)
