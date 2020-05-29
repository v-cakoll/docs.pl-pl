---
title: 'Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: 780a2c7fe240ed624ff106e8157661f8b76b32bd
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202373"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją

Rezerwacja adresu URL umożliwia ograniczenie użytkowników, którzy mogą odbierać wiadomości z adresu URL lub zestawu adresów URL. Rezerwacja składa się z szablonu adresu URL, listy kontroli dostępu (ACL) i zestawu flag. Szablon adresu URL określa adresy URL, na które ma wpływ rezerwacja. Aby uzyskać więcej informacji na temat sposobu przetwarzania szablonów adresów URL, zobacz [Routing przychodzących żądań](/windows/win32/http/routing-incoming-requests). Lista ACL kontroluje, jakiemu użytkownikowi lub grupie użytkowników można odbierać wiadomości z określonych adresów URL. Flagi wskazują, czy rezerwacja ma dać użytkownikowi lub grupie uprawnienie do nasłuchiwania bezpośrednio na adresie URL lub delegowania uprawnień do nasłuchiwania w innym procesie.  
  
 W ramach domyślnej konfiguracji systemu operacyjnego program Windows Communication Foundation (WCF) tworzy globalnie dostępną rezerwację dla portu 80, aby umożliwić wszystkim użytkownikom uruchamianie aplikacji korzystających z podwójnego powiązania protokołu HTTP na potrzeby komunikacji dwukierunkowej. Ponieważ lista kontroli dostępu dla tej rezerwacji jest dla wszystkich, Administratorzy nie mogą jawnie zezwolić na nasłuchiwanie adresu URL lub zestawu adresów URL ani nie zezwalać na nie. W tym temacie opisano sposób usuwania tej rezerwacji i ponownego tworzenia rezerwacji z ograniczoną listą ACL.  
  
W systemie Windows Vista lub Windows Server 2008 można wyświetlić wszystkie rezerwacje adresów URL protokołu HTTP z wiersza polecenia z podwyższonym poziomem uprawnień, wprowadzając polecenie `netsh http show urlacl` . W poniższym przykładzie przedstawiono sposób rezerwacji adresu URL programu WCF:

```
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```

 Rezerwacja składa się z szablonu adresu URL używanego, gdy aplikacja WCF używa podwójnego powiązania protokołu HTTP na potrzeby komunikacji dwukierunkowej. Adresy URL tego formularza są używane przez usługę WCF do wysyłania komunikatów z powrotem do klienta WCF podczas komunikacji przy użyciu podwójnego powiązania protokołu HTTP. Wszyscy uzyskują uprawnienia do nasłuchiwania na adresie URL, ale nie do delegowania nasłuchiwania w innym procesie. Na koniec lista ACL jest opisana w temacie Security Descriptor Definition Language (SSDL). Aby uzyskać więcej informacji na temat SSDL, zobacz [SSDL](/windows/win32/secauthz/security-descriptor-definition-language)  
  
## <a name="to-delete-the-wcf-url-reservation"></a>Aby usunąć rezerwację adresu URL programu WCF  
  
1. Kliknij przycisk **Start**, wskaż **Wszystkie programy**, kliknij przycisk **akcesoria**, kliknij prawym przyciskiem myszy pozycję **wiersz polecenia** , a następnie kliknij polecenie **Uruchom jako administrator** w wyświetlonym menu kontekstowym. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może zadawać uprawnienia do kontynuowania.  
  
2. Wpisz w `netsh http delete urlacl url=http://+:80/Temporary_Listen_Addresses/` oknie wiersza polecenia.  
  
3. Jeśli rezerwacja zostanie pomyślnie usunięta, zostanie wyświetlony następujący komunikat. **Pomyślnie usunięto rezerwację adresu URL**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Tworzenie nowej grupy zabezpieczeń i zastrzeżenia adresu URL z ograniczeniami  
 Aby zastąpić rezerwację adresu URL programu WCF ograniczoną rezerwacją, należy najpierw utworzyć nową grupę zabezpieczeń. Można to zrobić na jeden z dwóch sposobów: w wierszu polecenia lub w konsoli zarządzania komputerem. Wystarczy wykonać tę czynność.  
  
### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Aby utworzyć nową grupę zabezpieczeń z wiersza polecenia  
  
1. Kliknij przycisk **Start**, wskaż **Wszystkie programy**, kliknij przycisk **akcesoria**, kliknij prawym przyciskiem myszy pozycję **wiersz polecenia** , a następnie kliknij polecenie **Uruchom jako administrator** w wyświetlonym menu kontekstowym. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może zadawać uprawnienia do kontynuowania.  
  
2. Wpisz w `net localgroup "<security group name>" /comment:"<security group description>" /add` wierszu polecenia. Zastąpienie **\<security group name>** na nazwę grupy zabezpieczeń, którą chcesz utworzyć, oraz **\<security group description>** odpowiedni opis grupy zabezpieczeń.  
  
3. Jeśli grupa zabezpieczeń została utworzona pomyślnie, zostanie wyświetlony następujący komunikat. **Polecenie zostało wykonane pomyślnie.**  
  
### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Aby utworzyć nową grupę zabezpieczeń za pomocą konsoli zarządzania komputerem  
  
1. Kliknij przycisk **Start**, kliknij pozycję **Panel sterowania**, kliknij pozycję **Narzędzia administracyjne**, a następnie kliknij pozycję **Zarządzanie komputerem** , aby otworzyć konsolę Zarządzanie komputerem. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może zadawać uprawnienia do kontynuowania.  
  
2. Kliknij pozycję **Narzędzia systemowe**, kliknij pozycję **lokalni użytkownicy i grupy**, kliknij prawym przyciskiem myszy folder **grupy** , a następnie kliknij pozycję **Nowa grupa** w wyświetlonym menu kontekstowym. Wpisz **nazwę żądanej grupy**, **Opis** i inne szczegóły tej nowej grupy zabezpieczeń, a następnie kliknij przycisk **Utwórz** , aby utworzyć grupę zabezpieczeń.  
  
### <a name="to-create-the-restricted-url-reservation"></a>Aby utworzyć rezerwację adresu URL z ograniczeniami  
  
1. Kliknij przycisk **Start**, wskaż **Wszystkie programy**, kliknij przycisk **akcesoria**, kliknij prawym przyciskiem myszy pozycję **wiersz polecenia** , a następnie kliknij polecenie **Uruchom jako administrator** w wyświetlonym menu kontekstowym. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może zadawać uprawnienia do kontynuowania.  
  
2. Wpisz w `netsh http add urlacl url=http://+:80/Temporary_Listen_Addresses/ user="<machine name>\<security group name>` wierszu polecenia. Zastępowanie na **\<machine name>** nazwę komputera, na którym należy utworzyć grupę, oraz **\<security group name>** nazwę grupy zabezpieczeń, która została wcześniej utworzona.  
  
3. Jeśli rezerwacja zostanie utworzona pomyślnie, zostanie wyświetlony następujący komunikat. **Pomyślnie dodano rezerwację adresu URL**.
