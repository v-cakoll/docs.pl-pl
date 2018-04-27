---
title: Proces zatwierdzania dokumentu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45a6a6b2cd3bf790c8170cef6a6111ee7dd0b27b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="document-approval-process"></a>Proces zatwierdzania dokumentu
W tym przykładzie przedstawiono korzystanie z wielu Windows Workflow Foundation (WF) i [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcje razem. Razem wdrażają scenariusza proces zatwierdzania dokumentu. Aplikacja kliencka można przesyłać dokumenty do zatwierdzenia i zatwierdzić dokumenty. Aplikacja menedżera zatwierdzenia istnieje ułatwiających komunikację między klientami i do wymuszania reguł procesu zatwierdzania. Proces zatwierdzania jest przepływ pracy, który można wykonać kilka typów zatwierdzenia. Działania istnieje pobieranie jednego zatwierdzenia, zatwierdzenia kworum (procent zbiór osób zatwierdzających) i proces zatwierdzania złożonych, który składa się z kworum i jednego zatwierdzenia w sekwencji.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Na poniższym rysunku przedstawiono proces zatwierdzania dokumentu.  
  
 ![Proces zatwierdzania dokumentu](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")  
  
 Z perspektywy klienta zatwierdzenia proces funkcji w następujący sposób:  
  
1.  Jako użytkownik w systemie proces zatwierdzania zasubskrybowaniem przez klienta.  
  
2.  A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient wysyła do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi hostowanej przez aplikację menedżera zatwierdzenia.  
  
3.  Identyfikator unikatowy użytkownika jest zwracana do klienta. Klient może teraz uczestniczyć w procesów zatwierdzania.  
  
4.  Po połączone, klient może wysyłać dokumentu do zatwierdzenia przy użyciu pojedynczego kworum lub procesów zatwierdzania złożonych.  
  
5.  Kliknięto przycisk w interfejsie klienta, uruchamia wystąpienie przepływu pracy w kliencie hosta usługi przepływu pracy.  
  
6.  Przepływ pracy wysyła żądanie zatwierdzenia do zatwierdzenia aplikacji menedżera.  
  
7.  Menedżer przepływu pracy jest uruchamiany przepływ pracy w bok do reprezentowania procesu zatwierdzania.  
  
8.  Gdy przepływ pracy zatwierdzania manager wykonuje, wyniki są wysyłane do klienta.  
  
9. Klient wyświetla wyniki.  
  
10. Klient może odbierać żądania zatwierdzenia i odpowiedzi na żądanie w dowolnym momencie w czasie.  
  
11. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi hostowanej na kliencie może odbierać żądania zatwierdzenia z aplikacji Menedżera zatwierdzenia.  
  
12. Informacje dokumentu są przedstawione na kliencie do przeglądu.  
  
13. Użytkownika można zatwierdzić lub odrzucić dokumentu.  
  
14. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta służy do wysyłania odpowiedzi zatwierdzenia z powrotem do aplikacji Menedżera zatwierdzenia.  
  
 Z punktu widzenia aplikacji Menedżera zatwierdzenia zatwierdzenia proces funkcji w następujący sposób:  
  
1.  Klient żąda brać udziału w systemie procesu zatwierdzania.  
  
2.  A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi w Menedżerze zatwierdzania odbiera żądanie, jako część systemu procesu zatwierdzania.  
  
3.  Unikatowy identyfikator jest generowany dla klienta. Informacje użytkownika są przechowywane w bazie danych.  
  
4.  Unikatowy identyfikator jest wysyłany do użytkownika.  
  
5.  Żądania zatwierdzenia jest wyświetlany. Menedżer zatwierdzeń wykonuje proces zatwierdzania.  
  
6.  Żądania zatwierdzenia jest odbierany przez Menedżera zatwierdzeń uruchamianie nowego przepływu pracy.  
  
7.  W zależności od typu żądania (prosty, kworum lub złożonych) innej aktywności jest wykonywana.  
  
8.  Wyślij i Odbierz działania z korelacją są używane do wysyłania żądań zatwierdzenia do klienta do przeglądu i odbierania odpowiedzi.  
  
9. Wynik procesu zatwierdzania są wysyłane do klienta.  
  
## <a name="using-the-sample"></a>Przy użyciu próbki  
  
##### <a name="to-set-up-the-database"></a>Aby skonfigurować bazę danych  
  
1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] otworzyć wiersz polecenia z uprawnieniami administratora, przejdź do tego folderu DocumentApprovalProcess i uruchom Setup.cmd.  
  
##### <a name="to-set-up-the-application"></a>Aby skonfigurować aplikację  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania DocumentApprovalProcess.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, uruchom aplikację menedżera zatwierdzeń, klikając prawym przyciskiem myszy projekt ApprovalManager w **Eksploratora rozwiązań** i klikając **debugowania**->**Start**  nowe wystąpienie w menu kontekstowym.  
  
     Poczekaj na Menedżerze wyjścia z informacją, że jest gotowa.  
  
##### <a name="to-run-the-single-approval-scenario"></a>Aby uruchomić scenariusz jednego zatwierdzenia  
  
1.  Otwórz wiersz polecenia z uprawnieniami administratora.  
  
2.  Przejdź do katalogu, który zawiera rozwiązania.  
  
3.  Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj dwa wystąpienia ApprovalClient.exe.  
  
4.  Kliknij przycisk **odnajdywanie**, poczekaj na **subskrypcji** przycisk jest aktywny.  
  
5.  Wpisz dowolną nazwę użytkownika i kliknij przycisk **subskrypcji**. Dla jednego klienta, użyj `UserType1` i inny typ `UserType2`.  
  
6.  W `UserType1` klienta, wybierz jednego zatwierdzenia typu z menu rozwijanego i wpisz nazwę dokumentu i zawartości. Kliknij przycisk **zażądać zatwierdzenia**.  
  
7.  W `UserType2` pojawia się dokumentu oczekujące na zatwierdzenie klienta. Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**. Wyniki powinny pojawiać się w `UserType1` klienta.  
  
##### <a name="to-run-the-quorum-approval-scenario"></a>Aby uruchomić scenariusza zatwierdzania kworum  
  
1.  Otwórz wiersz polecenia z uprawnieniami administratora.  
  
2.  Przejdź do katalogu, który zawiera rozwiązania.  
  
3.  Przejdź do folderu ApprovalClient\Bin\Debug i wykonaj trzy wystąpienia ApprovalClient.exe.  
  
4.  Kliknij przycisk **odnajdywanie**, poczekaj na **subskrypcji** przycisk jest aktywny.  
  
5.  Wpisz dowolną nazwę użytkownika i kliknij przycisk **subskrypcji**. Dla jednego klienta, użyj `UserType1` i inny typ `UserType2`.  
  
6.  W `UserType1` klienta, wybierz opcję zatwierdzania kworum typu z menu rozwijanego i wpisz nazwę dokumentu i zawartości. Kliknij przycisk **zażądać zatwierdzenia**. To żądania wysyłane przez dwa `UserType2` klientów zatwierdzanie lub odrzucanie dokumentu. Zarówno podczas `UserType2` klienci muszą odpowiadać tylko jeden klient musi zatwierdzić dokumentu do zatwierdzenia.  
  
7.  W `UserType2` pojawia się dokumentu oczekujące na zatwierdzenie klientów. Zaznacz go i naciśnij klawisz **zatwierdzić** lub **Odrzuć**. Wyniki powinny pojawiać się w `UserType1` klienta.  
  
##### <a name="to-run-the-complex-approval-scenario"></a>Aby uruchomić scenariusza zatwierdzania złożonych  
  
1.  Otwórz wiersz polecenia z uprawnieniami administratora.  
  
2.  Przejdź do katalogu, który zawiera rozwiązania.  
  
3.  Przejdź do folderu ApprovalClient\Bin\Debug i wykonać cztery wystąpienia ApprovalClient.exe.  
  
4.  Kliknij przycisk **odnajdywanie**, poczekaj na **subskrypcji** przycisk jest aktywny.  
  
5.  Wpisz dowolną nazwę użytkownika i kliknij przycisk **subskrypcji**. Dla jednego klienta, użyj `UserType1`w dwóch używa typu `UserType2`i w przypadku ostatniego użycia `UserType3`.  
  
6.  W `UserType1` klienta, wybierz jednego zatwierdzenia typu z menu rozwijanego i wpisz nazwę dokumentu i zawartości. Kliknij przycisk **zażądać zatwierdzenia**.  
  
7.  W `UserType2` pojawia się dokumentu oczekujące na zatwierdzenie klientów. Zaznacz go i naciśnij klawisz **zatwierdzić**, dokument jest przekazywana do `UserType3` klienta.  
  
     Jeśli dokument zostanie zaakceptowane przez pierwszy `UserType2` kworum, dokument jest przekazywana do `UserType3` klienta.  
  
8.  Zatwierdzanie lub odrzucanie dokumentu z `UserType3` klienta. Wyniki powinny pojawiać się w `UserType1` klienta.  
  
##### <a name="to-clean-up"></a>Aby wyczyścić  
  
1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, przejdź do folderu DocumentApprovalProcess i uruchom Cleanup.cmd.