---
title: Zaawansowane zasady
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3dd941509c37618480a20530d3f5239750917e98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="advanced-policy"></a>Zaawansowane zasady
W tym przykładzie rozszerza próbki proste zasady. Oprócz rabat lokalną i reguły biznesowe rabatem w przykładzie proste zasady dodano kilka nowych zasad.  
  
 Dodana reguła wysokiej wartości, co umożliwia większy rabat zamówień wysokiej wartości. Jest podana wartość priorytetu jest mniejsza niż dwoma poprzednimi zasady tak, aby będzie Zastąp pole Rabat i mieć pierwszeństwo nad zarówno lokalną i reguły biznesowe rabatów.  
  
 Oblicz reguły całkowita jest także dodawane, który oblicza łączną liczbę na podstawie poziomu rabatów. Pokazuje sposób odwołania do metody zdefiniowanej w działaniu przepływu pracy, jak również sposób użycia innego działania. Ta zasada przedstawiono również łańcucha zachowanie, ponieważ będzie ona oceniane w każdej chwili zmiany pola rabatów. Ponadto metoda przypisywanie powoduje wyświetlanie RuleWriteAttribute dla metody CalculateTotal. Powoduje to wpływ na reguły (ErrorTotalRule) do ponownego obliczenia zawsze, gdy metoda jest wykonywany.  
  
 Ostatnia reguła dodaje to taki, który wykryje błędy (w tym przypadku Suma mniejszą od 0). W takim przypadku jest zatrzymywane wykonywanie zasad.  
  
 Na koniec `Console.Writeline` wywołania są dodawane jako akcje do każdej reguły, aby zapewnić lepszą widoczność do wykonywania reguł, podczas pokazywania również, czy istnieje możliwość dostępu do metody statyczne na odwołuje się do typów. Aby uzyskać informacje na reguły, które są wykonywane, można użyć również śledzenia.  
  
 Dostępne są następujące reguły używane w tym przykładzie:  
  
 **ResidentialDiscountRule:**  
  
 Jeśli OrderValue > 500 i CustomerType = lokalną  
  
 NASTĘPNIE rabat = 5%  
  
 **BusinessDiscountRule:**  
  
 Jeśli OrderValue > 10000 i CustomerType = biznesowa  
  
 NASTĘPNIE rabat = 10%  
  
 **HighValueDiscountRule:**  
  
 Jeśli OrderValue > 20000  
  
 NASTĘPNIE rabat = 15%  
  
 **TotalRule:**  
  
 Jeśli Discount > 0.  
  
 NASTĘPNIE CalculateTotal (OrderValue dyskontowa)  
  
 Suma ELSE = OrderValue  
  
 **ErrorTotalRule:**  
  
 Jeśli całkowita \< 0  
  
 NASTĘPNIE błąd = "Uruchamiany ErrorTotalRule;" Zatrzymanie  
  
 Szacowanie reguły i wykonywanie znajdują się również za pośrednictwem śledzenia i śledzenia.  
  
### <a name="to-build-the-sample"></a>Aby samodzielnie tworzyć przykładowy  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązania bez debugowania, naciskając klawisze CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
-   W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze AdvancedPolicy\bin\debug (lub w folderze \bin AdvancedPolicy dla używanej wersji programu Visual Basic przykładu) znajdujący się poniżej głównego folderu przykładowej.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Proste zasad](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
