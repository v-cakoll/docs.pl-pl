---
title: Proces zatwierdzania dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 34b63acaacde274210343a1135f3ed39a2df885e
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582713"
---
# <a name="document-approval-process"></a>Proces zatwierdzania dokumentu
Niniejszy przykład pokazuje użycie wielu funkcji Windows Workflow Foundation (WF) i Windows Communication Foundation (WCF) ze sobą. Razem mogą implementować scenariusza proces zatwierdzania dokumentu. Aplikacja kliencka można przesłać dokumenty do zatwierdzenia i zatwierdzić dokumenty. Aplikacja menedżera zatwierdzenia istnieje ułatwienie komunikacji między klientami i wymuszać reguły proces zatwierdzania. Proces zatwierdzania jest przepływ pracy, który może wykonać kilka typów zatwierdzenia. Działania ma korzystać z jednego zatwierdzenia, zatwierdzenia kworum (procent zestaw osób zatwierdzających) i proces zatwierdzania złożony, który składa się z kworum i jednego zatwierdzenia w sekwencji.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Na poniższym rysunku przedstawiono proces zatwierdzania dokumentu.  
  
 ![Proces zatwierdzania dokumentu](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")  
  
 Z perspektywy klienta zatwierdzenia proces funkcji w następujący sposób:  
  
1.  Jako użytkownik w systemie proces zatwierdzania zasubskrybowaniem przez klienta.  
  
2.  Klienta programu WCF wysyła do usługi WCF hostowanej przez aplikację Menedżer zatwierdzenia.  
  
3.  Unikatowy identyfikator użytkownika jest zwracana do klienta. Klient może teraz uczestniczyć w procesów zatwierdzania.  
  
4.  Po przyłączony, klient może wysyłać dokumentu do zatwierdzenia przy użyciu pojedynczego kworum lub procesów zatwierdzania złożone.  
  
5.  Po kliknięciu przycisku w interfejsie klienta uruchamia wystąpienie przepływu pracy w kliencie hosta usługi przepływu pracy.  
  
6.  Przepływ pracy wysyła żądanie zatwierdzenia do aplikacji Menedżer zatwierdzenia.  
  
7.  Usługa workflow manager uruchamia przepływ pracy na bok do reprezentowania proces zatwierdzania.  
  
8.  Gdy przepływ pracy zatwierdzania manager wykonuje, wyniki są odsyłane do klienta.  
  
9. Klient wyświetla wyniki.  
  
10. Klient może odbierać żądania zatwierdzenia i odpowiadać na żądania w dowolnym momencie w czasie.  
  
11. Usługi WCF hostowane na komputerze klienckim może odbierać żądania zatwierdzenia z aplikacji Menedżera zatwierdzenia.  
  
12. Informacje dokumentu są przedstawione na kliencie do przeglądu.  
  
13. Użytkownika można zatwierdzić lub odrzucić dokumentu.  
  
14. Klienta programu WCF służy do wysyłania odpowiedzi na żądanie zatwierdzenia do aplikacji Menedżer zatwierdzenia.  
  
 Z punktu widzenia aplikacji Menedżera zatwierdzenia zatwierdzenia proces funkcji w następujący sposób:  
  
1.  Klient żąda do wzięcia udziału w systemie proces zatwierdzania.  
  
2.  Usługi WCF w Menedżerze zatwierdzania odbiera żądanie jako część systemu proces zatwierdzania.  
  
3.  Unikatowy identyfikator jest generowany dla klienta. Informacje użytkownika są przechowywane w bazie danych.  
  
4.  Unikatowy identyfikator jest wysyłane z powrotem do użytkownika.  
  
5.  Żądanie zatwierdzenia jest wyświetlany. Menedżer zatwierdzeń wykonuje proces zatwierdzania.  
  
6.  Żądanie zatwierdzenia jest odbierane przez Menedżera zatwierdzeń od nowego przepływu pracy.  
  
7.  W zależności od typu żądania (prosty, kworum lub złożonych) jest wykonywana innego działania.  
  
8.  Wysyłania i odbierania działań z korelacją są używane do wysłania żądania zatwierdzenia do klienta do przeglądu i odbierania odpowiedzi.  
  
9. Wynik procesu zatwierdzania, są wysyłane do klienta.  
  
## <a name="using-the-sample"></a>Przy użyciu przykładu  
  
##### <a name="to-set-up-the-database"></a>Aby skonfigurować bazę danych  
  
1.  Z wiersza polecenia programu Visual Studio 2010 otwartych z uprawnieniami administratora przejdź do tego folderu DocumentApprovalProcess i uruchom plik Setup.cmd.  
  
##### <a name="to-set-up-the-application"></a>Aby skonfigurować aplikację  
  
1.  Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania DocumentApprovalProcess.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, uruchamianie aplikacji Menedżer zatwierdzeń, klikając prawym przyciskiem myszy projekt ApprovalManager w **Eksploratora rozwiązań** i klikając **debugowania**->**Start**  nowe wystąpienie z menu podręcznego.  
  
     Poczekaj, aż Menedżer wyjście z informacją, że jest gotowa.  
  
##### <a name="to-run-the-single-approval-scenario"></a>Aby uruchomić scenariusza z jednego zatwierdzenia  
  
1.  Otwórz wiersz polecenia z uprawnieniami administratora.  
  
2.  Przejdź do katalogu, który zawiera rozwiązanie.  
  
3.  Przejdź do folderu ApprovalClient\Bin\Debug, a następnie wykonaj dwa wystąpienia ApprovalClient.exe.  
  
4.  Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.  
  
5.  Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**. Dla jednego klienta, należy użyć `UserType1` i innych typów `UserType2`.  
  
6.  W `UserType1` klienta, wybierz typ z menu rozwijanego jednego zatwierdzenia a następnie wpisz nazwę dokumentu i zawartości. Kliknij przycisk **zażądać zatwierdzenia**.  
  
7.  W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klienta. Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**. Wyniki powinny pokazywać `UserType1` klienta.  
  
##### <a name="to-run-the-quorum-approval-scenario"></a>Aby uruchomić scenariusz zatwierdzania kworum  
  
1.  Otwórz wiersz polecenia z uprawnieniami administratora.  
  
2.  Przejdź do katalogu, który zawiera rozwiązanie.  
  
3.  Przejdź do folderu ApprovalClient\Bin\Debug oraz wykonania trzech wystąpień ApprovalClient.exe.  
  
4.  Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.  
  
5.  Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**. Dla jednego klienta użyj `UserType1` i innego typu `UserType2`.  
  
6.  W `UserType1` klienta, wybierz opcję zatwierdzenia kworum typ z menu rozwijanego a następnie wpisz nazwę dokumentu i zawartości. Kliknij przycisk **zażądać zatwierdzenia**. To żądania wysyłane przez dwa `UserType2` klientów zatwierdzenia lub odrzucenia dokumentu. Podczas gdy obie `UserType2` klienci muszą odpowiadać tylko jednego klienta muszą zatwierdzić dokument, aby mogła zostać zatwierdzone.  
  
7.  W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klientów. Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**. Wyniki powinny pokazywać `UserType1` klienta.  
  
##### <a name="to-run-the-complex-approval-scenario"></a>Aby uruchomić scenariusz zatwierdzania złożonych  
  
1.  Otwórz wiersz polecenia z uprawnieniami administratora.  
  
2.  Przejdź do katalogu, który zawiera rozwiązanie.  
  
3.  Przejdź do folderu ApprovalClient\Bin\Debug i wykonać cztery wystąpienia ApprovalClient.exe.  
  
4.  Kliknij przycisk **odnajdywanie**, poczekaj, aż **subskrybowania** przycisk jest aktywny.  
  
5.  Wpisz dowolną nazwę użytkownika, a następnie kliknij przycisk **subskrybowania**. Dla jednego klienta użyj `UserType1`w dwóch używa typu `UserType2`i ostatniego użycia `UserType3`.  
  
6.  W `UserType1` klienta, wybierz typ z menu rozwijanego jednego zatwierdzenia a następnie wpisz nazwę dokumentu i zawartości. Kliknij przycisk **zażądać zatwierdzenia**.  
  
7.  W `UserType2` pojawia się dokumentu oczekuje na zatwierdzenie klientów. Zaznacz go i naciśnij klawisz **zatwierdzić**, dokument jest przekazywany do `UserType3` klienta.  
  
     Jeśli dokument zostanie zatwierdzony przez pierwszy `UserType2` kworum, dokument jest przekazywany do `UserType3` klienta.  
  
8.  Zatwierdź lub Odrzuć dokument z `UserType3` klienta. Wyniki powinny pokazywać `UserType1` klienta.  
  
##### <a name="to-clean-up"></a>Aby wyczyścić  
  
1.  Z wiersza polecenia programu Visual Studio 2010 przejdź do folderu DocumentApprovalProcess i uruchom Cleanup.cmd.
