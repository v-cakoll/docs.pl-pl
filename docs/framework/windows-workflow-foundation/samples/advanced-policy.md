---
title: Zaawansowane zasady
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: becdc28affd877239474d6f0f007a480297bccb8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387892"
---
# <a name="advanced-policy"></a>Zaawansowane zasady
W tym przykładzie rozszerza przykładowe proste zasady. Oprócz rabat na wersję lokalną i zniżki firm z przykładu proste zasady dodano kilka nowych zasad.  
  
 Dodano regułę o wysokiej wartości, co umożliwia większym rabatem zamówienia o wysokiej wartości. Otrzymuje wartość priorytetu jest mniejsza niż dwie poprzednie reguły tak, aby będzie Zastąp pole Rabat na wersję i mieć pierwszeństwo nad zarówno lokalną i zniżki biznesowych.  
  
 Oblicz całkowity reguły jest także dodawane, który oblicza sumę, zależnie od poziomu rabat w wysokości. Pokazuje, jak odwoływać się do metody zdefiniowanej w działaniu przepływu pracy, a także jak używać innego działania. Ta zasada przedstawia również, że łańcuch zachowanie, ponieważ będzie on oceniane dowolnym zmiany pola Rabat w wysokości. Ponadto przypisywanie metody jest wyświetlana przy użyciu RuleWriteAttribute metody CalculateTotal. Powoduje to reguły których to dotyczy (ErrorTotalRule), który ma zostać ponownie obliczone zawsze wtedy, gdy pobiera wykonywania metody.  
  
 Ostatnia reguła dodane to taki, który wykrywa błędy (w tym przypadku Suma mniejszą niż 0). W takiej sytuacji wykonywanie zasadach zostało zatrzymane.  
  
 Na koniec `Console.Writeline` wywołania są dodawane jako akcji do każdej reguły, aby zapewnić lepszą widoczność do wykonywania reguły, podczas wyświetlania również, że możliwe jest dostęp do metod statycznych w przywoływane typy. Można także użyć śledzenia Aby uzyskać wgląd w zasady, które są wykonywane.  
  
 Dostępne są następujące reguły używane w tym przykładzie:  
  
 **ResidentialDiscountRule:**  
  
 Jeśli OrderValue > 500 i CustomerType = zamieszkania  
  
 NASTĘPNIE rabat w wysokości = 5%  
  
 **BusinessDiscountRule:**  
  
 Jeśli OrderValue > 10000 i CustomerType = biznesowych  
  
 NASTĘPNIE rabat w wysokości 10% =  
  
 **HighValueDiscountRule:**  
  
 Jeśli OrderValue > 20000  
  
 NASTĘPNIE rabat w wysokości = 15%  
  
 **TotalRule:**  
  
 Jeśli z rabatami > 0  
  
 NASTĘPNIE CalculateTotal (OrderValue rabatu)  
  
 ELSE łącznie = OrderValue  
  
 **ErrorTotalRule:**  
  
 Jeśli łączna liczba \< 0  
  
 NASTĘPNIE błąd = "Wyzwolone ErrorTotalRule;" Zatrzymanie  
  
 Ocenę reguł i wykonywanie znajdują się również za pośrednictwem śledzenia i śledzenia.  
  
### <a name="to-build-the-sample"></a>Aby skompilować przykład  
  
1.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Uruchom rozwiązanie bez debugowania, naciskając klawisze CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
-   W oknie wiersza polecenia zestawu SDK Uruchom plik .exe w folderze AdvancedPolicy\bin\debug (lub folder \bin AdvancedPolicy wersję przykładu w Visual Basic), który znajduje się poniżej głównego folderu dla przykładu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Proste zasady](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
