---
title: Instrukcje dotyczące zapory
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 3c94f0edbb244b6c378cc32f05c34fd029d253ff
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837847"
---
# <a name="firewall-instructions"></a>Instrukcje dotyczące zapory
Należy włączyć kilka portów lub programów w zaporze, aby umożliwić działanie przykładów Windows Communication Foundation (WCF). Wiele przykładów komunikuje się za pomocą portów z zakresu 8000-8003 i portu 9000. Zapora jest domyślnie włączona i uniemożliwia dostęp do tych portów. Aby włączyć zaporę dla przykładów, wykonaj jedną z następujących procedur, w zależności od wymagań i środowiska zabezpieczeń:  
  
- Opcja 1: interaktywnie Włącz próbki w trakcie działania. Nie wprowadzaj żadnych zmian w konfiguracji zapory i Kontynuuj, aby rozpocząć Kompilowanie i uruchamianie przykładów. Po uruchomieniu przykładu zostanie wyświetlone okno dialogowe **alert zabezpieczeń systemu Windows** . Przykładowy program można następnie dodać interaktywnie do listy odblokowanej. Korzystając z tej procedury, może być konieczne ponowne uruchomienie przykładu.  
  
- Opcja 2: Włącz z wyprzedzeniem przykładowe programy. Uruchom aplet **Panelu sterowania Zapory systemu Windows** i Włącz przykładowe programy, które zamierzasz uruchomić. Musisz najpierw skompilować programy, aby pliki wykonywalne istniały. Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze.  
  
- Opcja 3: Włącz z wyprzedzeniem zakres portów. Uruchom aplet **Panelu sterowania** **zapory systemu Windows** i włącz porty 80, 443, 8000-8003 i 9000, które są używane przez przykłady. Bardziej szczegółowe instrukcje można znaleźć w poniższej procedurze. Ta opcja jest mniej bezpieczna niż w przypadku innych, ponieważ umożliwia każdemu programowi korzystanie z tych portów, a nie tylko przykładów.  
  
 Jeśli nie masz pewności, której procedury użyć, wybierz pierwszą opcję. Jeśli używasz zapory od innego dostawcy, może być konieczne wprowadzenie podobnych zmian.  
  
> [!IMPORTANT]
> Zmiana konfiguracji zapory wpływa na bezpieczeństwo. Zalecamy zapisanie wprowadzonych zmian i ich usunięcie po zakończeniu pracy z przykładami.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Aby włączyć z wyprzedzeniem programy próbne  
  
1. Skompiluj przykład.  
  
2. Kliknij przycisk **Start**, kliknij polecenie **Uruchom**, a następnie wpisz `firewall.cpl`. Spowoduje to otwarcie apletu **Panelu sterowania Zapory systemu Windows** .  
  
    > [!NOTE]
    > Musisz mieć uprawnienia do zmiany ustawień zapory, aby uruchamiać próbki, które wymagają możliwości komunikowania się przez zaporę systemu Windows. Jeśli niektóre ustawienia zapory są niedostępne, a komputer jest połączony z domeną, administrator systemu może kontrolować te ustawienia za pomocą zasady grupy.  
  
3. Wykonaj jedną z następujących czynności, aby umożliwić programowi za pomocą zapory systemu Windows:  
  
    - W systemie Windows 7 lub Windows Server 2008 R2 kliknij opcję **Zezwól programowi lub funkcji za pomocą zapory systemu Windows**. Kliknij pozycję **Zmień ustawienia**, Zezwól na **inny program...** .  
  
    - W systemie Windows Vista lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)]kliknij pozycję **Zezwól programowi przez zaporę systemu Windows**.  
  
4. Na karcie **wyjątki** kliknij pozycję **Dodaj program**.  
  
5. Kliknij przycisk **Przeglądaj** i wybierz plik wykonywalny przykładu, który ma zostać uruchomiony.  
  
6. Powtórz kroki 4 i 5, dopóki nie dodasz plików wykonywalnych ze wszystkich przykładów, które planujesz uruchomić.  
  
7. Kliknij przycisk **OK** , aby zamknąć aplet Zapora.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Aby włączyć z wyprzedzeniem zakres portów  
  
1. Kliknij przycisk **Start**, kliknij polecenie **Uruchom**, a następnie wpisz `firewall.cpl`. Spowoduje to otwarcie apletu **Panelu sterowania Zapory systemu Windows** .  
  
2. W systemie Windows 7 lub Windows Server 2008 R2 wykonaj następujące kroki.  
  
    1. Kliknij pozycję **Ustawienia zaawansowane** w lewej kolumnie okna Zapora systemu Windows.  
  
    2. W lewej kolumnie kliknij pozycję **reguły ruchu przychodzącego** .  
  
    3. Kliknij pozycję **nowe reguły** w prawej kolumnie.  
  
    4. Wybierz pozycję **port** , a następnie kliknij przycisk **dalej**.  
  
    5. Wybierz opcję **TCP** i wprowadź `8000, 8001, 8002, 8003, 9000, 80, 443` w polu **określone porty lokalne** .  
  
    6. Kliknij przycisk **Dalej**.  
  
    7. Wybierz opcję **Zezwalaj na połączenie**, a następnie kliknij przycisk **dalej** .  
  
    8. Wybierz pozycję **domena** i **prywatny**, a następnie kliknij przycisk **dalej**.  
  
    9. Nadaj nazwę tej regule `WCF-WF 4.0 Samples`i kliknij przycisk **Zakończ**.  
  
    10. Kliknij pozycję **reguły ruchu wychodzącego** i powtórz kroki od c do h.  
  
3. W systemie Windows Vista lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)]wykonaj następujące kroki.  
  
    1. Kliknij pozycję **Zezwól programowi przez zaporę systemu Windows**.  
  
    2. Na karcie **wyjątki** kliknij pozycję **Dodaj port**.  
  
    3. Wprowadź nazwę, wprowadź 8000 jako numer portu, a następnie wybierz opcję **TCP** .  
  
    4. Kliknij przycisk **Zmień zakres** , wybierz opcję tylko **moja sieć** (podsieć), a następnie kliknij przycisk **OK**.  
  
    5. Powtórz kroki od b do d dla portów 8001, 8002, 8003, 9000, 80 i 443.  
  
4. Kliknij przycisk **OK** , aby zamknąć aplet Zapora.  
  
> [!NOTE]
> Usuń wszystkie wyjątki zapory po zakończeniu pracy z przykładami. W tym celu należy otworzyć aplet **Panelu sterowania Zapory systemu Windows** i usunąć wszystkie programy lub wpisy portów, które zostały dodane przez poprzednie procedury.
