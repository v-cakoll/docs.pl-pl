---
title: 'Instrukcje: zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: 981c4890b11130b937e176da78f378340c0d3894
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991662"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Instrukcje: zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją
Rezerwacja adresu URL umożliwia ograniczenie użytkowników, którzy mogą odbierać wiadomości z adresu URL lub zestawu adresów URL. Rezerwacja składa się z szablonu adresu URL, listy kontroli dostępu (ACL) i zestawu flag. Szablon adresu URL określa adresy URL, na które ma wpływ rezerwacja. Aby uzyskać więcej informacji na temat sposobu przetwarzania szablonów adresów URL, zobacz [Routing przychodzących żądań](https://go.microsoft.com/fwlink/?LinkId=136764). Lista ACL kontroluje, jakiemu użytkownikowi lub grupie użytkowników można odbierać wiadomości z określonych adresów URL. Flagi wskazują, czy rezerwacja ma dać użytkownikowi lub grupie uprawnienie do nasłuchiwania bezpośrednio na adresie URL lub delegowania uprawnień do nasłuchiwania w innym procesie.  
  
 W ramach domyślnej konfiguracji systemu operacyjnego program Windows Communication Foundation (WCF) tworzy globalnie dostępną rezerwację dla portu 80, aby umożliwić wszystkim użytkownikom uruchamianie aplikacji korzystających z podwójnego powiązania protokołu HTTP na potrzeby komunikacji dwukierunkowej. Ponieważ lista kontroli dostępu dla tej rezerwacji jest dla wszystkich, Administratorzy nie mogą jawnie zezwolić na nasłuchiwanie adresu URL lub zestawu adresów URL ani nie zezwalać na nie. W tym temacie opisano sposób usuwania tej rezerwacji i ponownego tworzenia rezerwacji z ograniczoną listą ACL.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] stronie [!INCLUDE[lserver](../../../../includes/lserver-md.md)] lub można wyświetlić wszystkie rezerwacje adresów URL protokołu HTTP z wiersza polecenia z podwyższonym poziomem `netsh http show urlacl`uprawnień, wpisując polecenie.  W poniższym przykładzie pokazano, co powinno być podobne do rezerwacji adresu URL programu WCF.  

```
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```

 Rezerwacja składa się z szablonu adresu URL używanego, gdy aplikacja WCF używa podwójnego powiązania protokołu HTTP na potrzeby komunikacji dwukierunkowej. Adresy URL tego formularza są używane przez usługę WCF do wysyłania komunikatów z powrotem do klienta WCF podczas komunikacji przy użyciu podwójnego powiązania protokołu HTTP. Wszyscy uzyskują uprawnienia do nasłuchiwania na adresie URL, ale nie do delegowania nasłuchiwania w innym procesie. Na koniec lista ACL jest opisana w temacie Security Descriptor Definition Language (SSDL). Aby uzyskać więcej informacji na temat SSDL, zobacz [SSDL](https://go.microsoft.com/fwlink/?LinkId=136789)  
  
## <a name="to-delete-the-wcf-url-reservation"></a>Aby usunąć rezerwację adresu URL programu WCF  
  
1. Kliknij przycisk **Start**, wskaż **Wszystkie programy**, kliknij przycisk **akcesoria**, kliknij prawym przyciskiem myszy pozycję **wiersz polecenia** , a następnie kliknij polecenie **Uruchom jako administrator** w wyświetlonym menu kontekstowym. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może zadawać uprawnienia do kontynuowania.  
  
2. W oknie wiersza polecenia wpisz polecenie **netsh http http://+:80/Temporary_Listen_Addresses/ Delete urlacl URL =** .  
  
3. Jeśli rezerwacja zostanie pomyślnie usunięta, zostanie wyświetlony następujący komunikat. **Pomyślnie usunięto rezerwację adresu URL**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Tworzenie nowej grupy zabezpieczeń i zastrzeżenia adresu URL z ograniczeniami  
 Aby zastąpić rezerwację adresu URL programu WCF ograniczoną rezerwacją, należy najpierw utworzyć nową grupę zabezpieczeń. Można to zrobić na jeden z dwóch sposobów: w wierszu polecenia lub w konsoli zarządzania komputerem. Wystarczy wykonać tę czynność.  
  
### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Aby utworzyć nową grupę zabezpieczeń z wiersza polecenia  
  
1. Kliknij przycisk **Start**, wskaż **Wszystkie programy**, kliknij przycisk **akcesoria**, kliknij prawym przyciskiem myszy pozycję **wiersz polecenia** , a następnie kliknij polecenie **Uruchom jako administrator** w wyświetlonym menu kontekstowym. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może zadawać uprawnienia do kontynuowania.  
  
2. Wpisz w polu **net localgroup "\<nazwa grupy zabezpieczeń >"/comment: "\<opis grupy zabezpieczeń >"/Add** w wierszu polecenia. Zamienianie  **\<nazwy grupy zabezpieczeń >** na nazwę grupy zabezpieczeń, którą chcesz utworzyć, i  **\<opis grupy** zabezpieczeń, > z odpowiednim opisem dla grupy zabezpieczeń.  
  
3. Jeśli grupa zabezpieczeń została utworzona pomyślnie, zostanie wyświetlony następujący komunikat. **Polecenie zostało wykonane pomyślnie.**  
  
### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Aby utworzyć nową grupę zabezpieczeń za pomocą konsoli zarządzania komputerem  
  
1. Kliknij przycisk **Start**, kliknij pozycję **Panel sterowania**, kliknij pozycję **Narzędzia administracyjne**, a następnie kliknij pozycję **Zarządzanie komputerem** , aby otworzyć konsolę Zarządzanie komputerem. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może zadawać uprawnienia do kontynuowania.  
  
2. Kliknij pozycję **Narzędzia systemowe**, kliknij pozycję **lokalni użytkownicy i grupy**, kliknij prawym przyciskiem myszy folder **grupy** , a następnie kliknij pozycję **Nowa grupa** w wyświetlonym menu kontekstowym. Wpisz **nazwę żądanej grupy**, **Opis** i inne szczegóły tej nowej grupy zabezpieczeń, a następnie kliknij przycisk **Utwórz** , aby utworzyć grupę zabezpieczeń.  
  
### <a name="to-create-the-restricted-url-reservation"></a>Aby utworzyć rezerwację adresu URL z ograniczeniami  
  
1. Kliknij przycisk **Start**, wskaż **Wszystkie programy**, kliknij przycisk **akcesoria**, kliknij prawym przyciskiem myszy pozycję **wiersz polecenia** , a następnie kliknij polecenie **Uruchom jako administrator** w wyświetlonym menu kontekstowym. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może zadawać uprawnienia do kontynuowania.  
  
2. Wpisz polecenie **netsh http Add urlacl URL =http://+:80/Temporary_Listen_Addresses/ User = "\< Machine Name >\\ < nazwa\> grupy zabezpieczeń** w wierszu polecenia. Zastępowanie  **\<nazwy maszyny >** nazwą komputera, na którym należy utworzyć grupę, oraz  **\<nazwę grupy zabezpieczeń >** nazwą grupy zabezpieczeń, która została wcześniej utworzona.  
  
3. Jeśli rezerwacja zostanie utworzona pomyślnie, zostanie wyświetlony następujący komunikat. **Pomyślnie dodano rezerwację adresu URL**.
