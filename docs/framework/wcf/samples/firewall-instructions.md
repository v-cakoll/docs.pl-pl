---
title: Instrukcje dotyczące zapory
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 06e5ba64ab0ec3558e4c773c9cb21f961384e0c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650039"
---
# <a name="firewall-instructions"></a>Instrukcje dotyczące zapory
Należy włączyć kilka portów i programów w zaporze, aby mógł działać przykładów Windows Communication Foundation (WCF). Wiele przykładów komunikują się przy użyciu portów z zakresu 8000-8003 i portu 9000. Zapora jest włączona domyślnie i uniemożliwia dostęp do tych portów. Aby włączyć zaporę dla próbki, wykonaj jedną z następujących procedur, w zależności od wymagań i środowisko zabezpieczeń:  
  
- Option 1: Włącz interakcyjne przykładów podczas pracy. Wprowadzone żadne zmiany zaawansowane konfiguracja zapory i przejdź do rozpocząć tworzenie i uruchamianie przykładów programu. Po uruchomieniu przykładu **Alert zabezpieczeń Windows** pojawi się okno dialogowe. Z przykładowego program można dodać interaktywnie do listy odblokowane. Przy użyciu tej procedury trzeba ponownie uruchom przykład.  
  
- Option 2: Włącz przykładowe programy z wyprzedzeniem. Rozpocznij **Panelu sterowania zapory Windows** apletu i Włącz przykładowe programy plan do uruchomienia. Należy najpierw utworzyć programy, dzięki czemu istnieją pliki wykonywalne. Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.  
  
- Opcja 3: Włącz zakres portów z wyprzedzeniem. Rozpocznij **zapory Windows** **Panelu sterowania** apletu i Włącz porty 80, 443, 8000 8003 oraz 9000, które są używane przez próbki. Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze. Ta opcja jest mniej bezpieczna niż inne, ponieważ zezwala ona na dowolnym programowi na używanie tych portów, a nie tylko przykłady.  
  
 Jeśli masz pewności, której procedury należy użyć, wybierz opcję pierwszym. Jeśli korzystasz z zapory, od innego dostawcy, konieczne może wprowadzić zmiany podobne.  
  
> [!IMPORTANT]
>  Zmiana konfiguracji zapory ma wpływ na bezpieczeństwo. Zaleca się zapisanie zmian upewnij i usuń je, po zakończeniu pracy z przykładów.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Aby włączyć programy przykłady z wyprzedzeniem  
  
1. Skompiluj przykład.  
  
2. Kliknij przycisk **Start**, kliknij przycisk **Uruchom**i wpisz `firewall.cpl`. Spowoduje to otwarcie **Panelu sterowania zapory Windows** apletu.  
  
    > [!NOTE]
    >  Musi mieć uprawnienia do zmiany ustawień zapory, aby uruchomić przykłady, które muszą mieć możliwość komunikowania się przez zaporę Windows. Jeśli niektóre ustawienia zapory są niedostępne, a komputer jest podłączony do domeny, administrator systemu może kontrolowanie tych ustawień za pomocą zasad grupy.  
  
3. Wykonaj jedną z następujących czynności określonego działania umożliwiające programu przez zaporę Windows:  
  
    - Windows 7 lub Windows Server 2008 r2, wybierz polecenie **Zezwalaj programowi lub funkcję przez zaporę Windows**. Kliknij przycisk **zmiany ustawień**, Zezwalaj na **inny Program...** .  
  
    - Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], kliknij przycisk **Zezwól programu przez zaporę Windows**.  
  
4. Na **wyjątki** kliknij pozycję **Dodaj Program**.  
  
5. Kliknij przycisk **Przeglądaj** i wybierz plik wykonywalny próbki mają być uruchamiane.  
  
6. Powtórz kroki 4 i 5, aż zostaną dodane pliki wykonywalne przykładów, które mają być uruchamiane.  
  
7. Kliknij przycisk **OK** zamknąć aplet Zapora.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Aby włączyć zakres portów z wyprzedzeniem  
  
1. Kliknij przycisk **Start**, kliknij przycisk **Uruchom**i wpisz `firewall.cpl`. Spowoduje to otwarcie **Panelu sterowania zapory Windows** apletu.  
  
2. Windows 7 lub Windows Server 2008 R2 wykonaj następujące kroki.  
  
    1. Kliknij przycisk **Zaawansowane ustawienia** w lewej kolumnie okna zapory Windows.  
  
    2. Kliknij przycisk **reguły ruchu przychodzącego** w lewej kolumnie.  
  
    3. Kliknij przycisk **nowe reguły** w prawej kolumnie.  
  
    4. Wybierz **portu** i kliknij przycisk **dalej**.  
  
    5. Wybierz **TCP** i wprowadź `8000, 8001, 8002, 8003, 9000, 80, 443` w **określone porty lokalne** pola.  
  
    6. Kliknij przycisk **Dalej**.  
  
    7. Wybierz **Zezwalaj na połączenie**i kliknij przycisk **dalej** .  
  
    8. Wybierz **domeny** i **prywatnej**i kliknij przycisk **dalej**.  
  
    9. Nazwa ta reguła `WCF-WF 4.0 Samples`i kliknij przycisk **Zakończ**.  
  
    10. Kliknij przycisk **reguł dla ruchu wychodzącego** i powtórz kroki od c-h.  
  
3. Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], wykonaj następujące kroki.  
  
    1. Kliknij przycisk **Zezwól programu przez zaporę Windows**.  
  
    2. Na **wyjątki** kliknij pozycję **Dodaj Port**.  
  
    3. Wprowadź nazwę, wprowadź numer portu 8000, a następnie wybierz **TCP** opcji.  
  
    4. Kliknij przycisk **zmiana zakresu** przycisku Wybierz **Moja sieć** jedyną opcją (podsieć), a następnie kliknij przycisk **OK**.  
  
    5. Powtórz kroki od b do d dla portów 8001, 8002 8003, 9000, 80 i 443.  
  
4. Kliknij przycisk **OK** zamknąć aplet Zapora.  
  
> [!NOTE]
>  Po zakończeniu pracy z próbki, należy usunąć wszelkie wyjątki zapory. Aby to zrobić, otwórz **Panelu sterowania zapory Windows** apletu i Usuń wszystkie programy lub portu wpisów, które zostały dodane przez poprzedniej procedury.
