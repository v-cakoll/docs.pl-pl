---
title: Przykład elementu UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 15799c1aaf3ed7df5f7721368dea426665dcf335
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044598"
---
# <a name="uritemplate-sample"></a>Przykład elementu UriTemplate
<xref:System.UriTemplate> Klasa zawiera metody pracy z zestawami identyfikatorów URI, które mają wspólną strukturę. Ten przykład ilustruje następujące kluczowe pojęcia dotyczące `UriTemplate`:  
  
- Składnia służąca do tworzenia szablonów.  
  
- Tworzenie wystąpienia identyfikatorów URI z `UriTemplate` użyciem <xref:System.UriTemplate.BindByName%2A> i <xref:System.UriTemplate.BindByPosition%2A>.  
  
- <xref:System.UriTemplateTable.Match%2A>, która jest operacją `BindByName` odwrotną i. `BindByPosition`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a>Zobacz także

- [Tabela UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [Dyspozytor tabeli UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
