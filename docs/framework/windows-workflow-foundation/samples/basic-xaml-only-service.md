---
title: Tylko usługi podstawowe języka XAML
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: aa6b6ec6930ac90fe95b1cdfcd4cb027de8e5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517202"
---
# <a name="basic-xaml-only-service"></a>Tylko usługi podstawowe języka XAML
W tym przykładzie pokazano, jak utworzyć usługę tylko XAML. Scenariusz jest usługą Diagnostyka dla problemów związanych z samochodów. Usługa jest wdrażana jako przepływ pracy, która najpierw zadaje szereg pytań, aby zdiagnozować problem klienta. Istnieją dwa typy usługi diagnozować problemy (samochód się nie uruchomić lub klimatyzacja nie działa). Przepływ pracy używa szablonu żądania/odpowiedzi przy użyciu projektanta do udostępnienia trzy operacje usługi simple. Usługa znajduje się w usługach IIS przez tworzenie katalogu wirtualnego w usługach IIS i kopiowanie service1.xamlx i plikach Web.config w katalogu wirtualnego, nie skompilowanego kodu jest wymagane. Domyślnie ten przykład automatycznie skopiuje pliki potrzebne do utworzenia, wykonaj instrukcje instalacji dla przykładów WCF i WF katalogu wirtualnego: [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) podczas tworzenia w programie Visual Studio 2010.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załadowanie projektu rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompilować projekt.  
  
2.  Uruchom aplikację klienta wygenerowanego w \Client\bin\debug [katalogu podstawowego rozwiązania].  
  
3.  Aplikacja do drukowania opcje wybiera opcję. Następnie aplikacja prosi pytaniami odpowiedzieć tak lub nie (przy użyciu kluczy T/N). Po zakończeniu jest usługa diagnozowanie problemów, drukowania diagnostyki aplikacji.  
  
4.  Aplikacja Przechodzi wstecz do opcji. Można zdiagnozować problem innego lub zamknij aplikację.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`