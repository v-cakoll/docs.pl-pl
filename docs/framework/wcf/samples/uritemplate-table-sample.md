---
title: Przykład tabeli UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: c0aed1a49faf74ab9fd463769aab66ad72e74038
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183264"
---
# <a name="uritemplate-table-sample"></a>Przykład tabeli UriTemplate
Klasa <xref:System.UriTemplateTable> zawiera słownika jak struktury tabeli asocjacyjnych do pracy z zestawem `UriTemplate` wystąpień. Określone jednolite identyfikatory zasobów (URI) można skutecznie dopasować do wszystkich szablonów w tabeli, a dane skojarzone z dopasowanym szablonem mogą być pobierane.  
  
 W tym przykładzie przedstawiono następujące `UriTemplateTable` kluczowe pojęcia związane z klasą:  
  
- Składnia tworzenia wystąpienia pliku `UriTemplateTable`.  
  
- Wypełnianie a `UriTemplateTable` zestawem par kluczy/wartości.  
  
- Dopasowywanie identyfikatora URI kandydata do tabeli przy użyciu programu <xref:System.UriTemplateTable.MatchSingle%2A>.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>Zobacz też

- [Dyspozytor tabeli UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
