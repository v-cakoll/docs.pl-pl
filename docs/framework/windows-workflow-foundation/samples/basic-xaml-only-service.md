---
title: Jedyna usługa podstawowe XAML
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: f4f296a97b9c3093874c5ec8e05023e84b0af44a
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489750"
---
# <a name="basic-xaml-only-service"></a>Jedyna usługa podstawowe XAML
W tym przykładzie pokazano, jak utworzyć usługę tylko XAML. Scenariusz jest usługą diagnostyki dla problemów związanych z samochodów. Usługa jest wdrażana jako przepływ pracy, która najpierw zadaje szereg pytań, aby zdiagnozować problem klienta. Istnieją dwa typy usługi można zdiagnozować problemy (samochód się nie uruchomić lub klimatyzacja nie działa). Przepływ pracy używa szablonu żądanie/nietypizowana odpowiedź przy użyciu projektanta w celu udostępnienia trzech operacji prostą usługę. Usługa jest hostowana w usługach IIS przez tworzenie katalogów wirtualnych w usługach IIS i kopiowanie service1.xamlx i plikach Web.config w katalogu wirtualnego, skompilowany jest wymagany żaden kod. Domyślnie w tym przykładzie zostanie automatycznie skopiuj do niego potrzebne pliki katalog wirtualny utworzony podczas wykonaj instrukcje dotyczące instalacji, przykłady programu WCF i WF: [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) podczas kompilowania w programie Visual Studio 2010.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załaduj projekt rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompiluj projekt.  
  
2.  Uruchom aplikację klienta generowane w \Client\bin\debug [katalog podstawowy rozwiązania].  
  
3.  Aplikacja wyświetla opcje, wybiera opcję. Następnie aplikacja zadaje pytania, odpowiadać tak lub nie (przy użyciu kluczy T/N). Po zakończeniu usługi diagnozowania problemów, wyświetla diagnostyki aplikacji.  
  
4.  Aplikacja powróci do opcji. Można zdiagnozować problem inny lub zamknij aplikację.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`