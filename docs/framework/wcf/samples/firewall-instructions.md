---
title: "Instrukcje dotyczące zapory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 270df09f709dfdfeb78b9bd72bc3744c6614bc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="firewall-instructions"></a>Instrukcje dotyczące zapory
Należy włączyć kilka portów lub programów w zaporze, tak że [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] próbki mogą działać. Wiele próbek komunikują się przy użyciu portów w zakresie 8000-8003 i portu 9000. Zapora jest włączona domyślnie i uniemożliwia dostęp do tych portów. Aby włączyć zapory próbek, wykonaj jedną z następujących procedur, w zależności od wymagań i środowisko zabezpieczeń:  
  
-   Opcja 1: Włącz interakcyjne przykłady podczas pracy. Nie wprowadzisz wcześniejszym zmian do konfiguracji zapory i przejdź do zacząć tworzyć i uruchamiać próbek. Po uruchomieniu próbkę **Alert zabezpieczeń systemu Windows** zostanie wyświetlone okno dialogowe. Przykładowy program zagrożona można dodać interaktywnie do listy odblokowany. Ta procedura może być ponowne uruchomienie przykładu.  
  
-   Opcja 2: Włączanie przykładowe programy z wyprzedzeniem. Uruchom **Panelu sterowania Zapory systemu Windows** apletu i włączyć plan do uruchamiania programów próbki. Programy należy utworzyć najpierw, więc istnieje plików wykonywalnych. Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.  
  
-   Opcja 3: Włącz zakres portów z wyprzedzeniem. Uruchom **zapory systemu Windows** **Panelu sterowania** apletu i Włącz porty 80, 443, 8000 8003 i 9000, które są używane przez próbek. Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze. Ta opcja jest mniej bezpieczne od innych, ponieważ zezwala ona na dowolnym programem na te porty, nie tylko próbek.  
  
 Masz pewności, procedurę do użycia, jeśli pierwsza opcja. Jeśli korzystasz z zapory od innego dostawcy, konieczne może być podobne zmiany.  
  
> [!IMPORTANT]
>  Zmiana konfiguracji zapory ma wpływ na bezpieczeństwo. Zalecane jest zapisanie zmian należy i usuń je po zakończeniu pracy z próbek.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Aby włączyć programy próbki z wyprzedzeniem  
  
1.  Tworzenie przykładowej.  
  
2.  Kliknij przycisk **Start**, kliknij przycisk **Uruchom**i wpisz `firewall.cpl`. Spowoduje to otwarcie **Panelu sterowania Zapory systemu Windows** apletu.  
  
    > [!NOTE]
    >  Musi mieć uprawnienia do zmiany ustawień zapory, aby uruchomić przykłady, które muszą mieć możliwość komunikacji za pośrednictwem zapory systemu Windows. Jeśli niektóre ustawienia zapory są niedostępne, a komputer jest podłączony do domeny, administrator systemu może kontroluje te ustawienia za pomocą zasad grupy.  
  
3.  Wykonaj jedną z następujących kroków określonego działania umożliwia programu przez zaporę systemu Windows:  
  
    -   W systemie Windows 7 lub Windows Server 2008 r2, kliknij polecenie **Zezwalaj programowi lub funkcji przez zaporę systemu Windows**. Kliknij przycisk **zmienić ustawienia**, Zezwalaj **inny Program...** .  
  
    -   Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], kliknij przycisk **Zezwól programu przez zaporę systemu Windows**.  
  
4.  Na **wyjątki** , kliknij pozycję **Dodaj Program**.  
  
5.  Kliknij przycisk **Przeglądaj** i wybrać plik wykonywalny próbki ma zostać uruchomiona.  
  
6.  Powtórz kroki 4 i 5, aż zostaną dodane pliki wykonywalne próbek, który ma zostać uruchomiona.  
  
7.  Kliknij przycisk **OK** zamknąć aplet zapory.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Aby włączyć zakres portów z wyprzedzeniem  
  
1.  Kliknij przycisk **Start**, kliknij przycisk **Uruchom**i wpisz `firewall.cpl`. Spowoduje to otwarcie **Panelu sterowania Zapory systemu Windows** apletu.  
  
2.  W systemie Windows 7 lub Windows Server 2008 R2 wykonaj następujące kroki.  
  
    1.  Kliknij przycisk **Zaawansowane ustawienia** w lewej kolumnie okna zapory systemu Windows.  
  
    2.  Kliknij przycisk **reguły ruchu przychodzącego** w lewej kolumnie.  
  
    3.  Kliknij przycisk **nowe reguły** w prawej kolumnie.  
  
    4.  Wybierz **portu** i kliknij przycisk **dalej**.  
  
    5.  Wybierz **TCP** , a następnie wprowadź `8000, 8001, 8002, 8003, 9000, 80, 443` w **określone porty lokalne** pola.  
  
    6.  Kliknij przycisk **Dalej**.  
  
    7.  Wybierz **zezwalały na połączenie**i kliknij przycisk **dalej** .  
  
    8.  Wybierz **domeny** i **prywatnej**i kliknij przycisk **dalej**.  
  
    9. Nazwę tej reguły `WCF-WF 4.0 Samples`i kliknij przycisk **Zakończ**.  
  
    10. Kliknij przycisk **reguły wychodzące** i powtórz kroki od c-h.  
  
3.  Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], wykonaj następujące kroki.  
  
    1.  Kliknij przycisk **Zezwól programu przez zaporę systemu Windows**.  
  
    2.  Na **wyjątki** , kliknij pozycję **Dodaj Port**.  
  
    3.  Wprowadź nazwę, wprowadź 8000 jako numer portu, a następnie wybierz **TCP** opcji.  
  
    4.  Kliknij przycisk **Zmień zakres** przycisku Wybierz **Moja sieć** tylko opcja (podsieć), a następnie kliknij przycisk **OK**.  
  
    5.  Powtórz kroki od b-d dla portów 8001, 8002, 8003 9000, 80 i 443.  
  
4.  Kliknij przycisk **OK** zamknąć aplet zapory.  
  
> [!NOTE]
>  Po zakończeniu pracy z próbki, należy usunąć wszelkie wyjątki zapory. Aby to zrobić, otwórz **Panelu sterowania Zapory systemu Windows** apletu i Usuń wszystkie programy lub portu wpisów, które zostały dodane w ramach poprzednich procedur.
