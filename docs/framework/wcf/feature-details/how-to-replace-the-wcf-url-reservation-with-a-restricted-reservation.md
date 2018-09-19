---
title: 'Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją'
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: b53596d7ac4e7e7c3748f6a98130492a96c0b48c
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288358"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją
Rezerwację adresu URL pozwala ograniczyć, kto może odbierać komunikaty z adresem URL lub zbiór adresów URL. Rezerwacja składa się z szablonem adresu URL, listy kontroli dostępu (ACL) i zestaw flag. Szablon adresu URL definiuje które adresy URL dotyczy rezerwacji. Aby uzyskać więcej informacji na temat sposobu przetwarzania szablonów URL zobacz [routingu żądań przychodzących](https://go.microsoft.com/fwlink/?LinkId=136764). Listy kontroli dostępu kontroluje, jakie użytkownik lub grupa użytkowników może odbierać komunikaty z określonych adresów URL. Flagi wskazują, czy rezerwacja ma przyznać uprawnienia użytkownika lub grupy do nasłuchiwania na adres URL, bezpośrednio lub Aby delegować uprawnienia do nasłuchiwania jakiś inny proces.  
  
 Częścią domyślnej konfiguracji systemu operacyjnego Windows Communication Foundation (WCF) tworzy globalnie dostępne rezerwacji dla portu 80, aby umożliwić wszystkim użytkownikom na uruchamianie aplikacji, które używają podwójną wiązanie HTTP na komunikację dupleksową. Ponieważ listy ACL na tę rezerwację dla wszystkich użytkowników, administratorów nie może jawnie Zezwalaj lub nie zezwalaj uprawnienia do nasłuchiwania na adres URL lub zestaw adresów URL. W tym temacie opisano sposób usuwania tego zastrzeżenia oraz sposób ponownie utworzyć zastrzeżenie z ograniczeniami listy ACL.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)] wyświetlać wszystkie rezerwacje adresu URL HTTP z wiersza polecenia z podwyższonym poziomem uprawnień, wpisując `netsh http show urlacl`.  Poniższy przykład pokazuje, co powinno przypominać rezerwację adresu URL programu WCF.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 Rezerwacja składa się z szablonu adresu URL używany, gdy aplikacji WCF używa podwójnego powiązanie HTTP do komunikację dupleksową. Adresy URL tego formularza są używane dla usługi WCF do wysyłania komunikatów z powrotem do klienta platformy WCF podczas komunikowania się za pośrednictwem dwa powiązania protokołu HTTP. Wszyscy jest uprawnienie do nasłuchiwania na adres URL, ale nie delegować nasłuchiwania na inny proces. Na koniec listy ACL jest opisana w języka definicji deskryptorów zabezpieczeń (SSDL). Aby uzyskać więcej informacji na temat SSDL zobacz [SSDL](https://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>Aby usunąć zastrzeżenie adresu URL programu WCF  
  
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij prawym przyciskiem myszy **polecenia** i kliknij przycisk **Uruchom jako Administrator** z menu kontekstowego, który pojawia się. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może poprosić uprawnień, aby kontynuować.  
  
2.  Wpisz **netsh http usunąć adres url urlacl =http://+:80/Temporary_Listen_Addresses/**  w oknie wiersza polecenia.  
  
3.  Jeśli rezerwacji został pomyślnie usunięty, jest wyświetlany następujący komunikat. **Pomyślnie usunięto rezerwację adresu URL**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Tworzenie nowej grupy zabezpieczeń i nową rezerwację adresu URL ograniczone  
 Aby zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją, należy najpierw utworzyć nową grupę zabezpieczeń. Można to zrobić na dwa sposoby: z wiersza polecenia lub w konsoli zarządzania komputerem. Trzeba wykonać jedną.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Aby utworzyć nową grupę zabezpieczeń z poziomu wiersza polecenia  
  
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij prawym przyciskiem myszy **polecenia** i kliknij przycisk **Uruchom jako Administrator** z menu kontekstowego, który pojawia się. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może poprosić uprawnień, aby kontynuować.  
  
2.  Wpisz **net localgroup "\<Nazwa grupy zabezpieczeń >" / comment: "\<opis grupy zabezpieczeń >" / add** w wierszu polecenia. Zastępowanie  **\<Nazwa grupy zabezpieczeń >** o nazwie grupy zabezpieczeń, którą chcesz utworzyć i  **\<opis grupy zabezpieczeń >** przy użyciu odpowiedniego opis Grupa zabezpieczeń.  
  
3.  Jeśli grupa zabezpieczeń została utworzona pomyślnie, jest wyświetlany następujący komunikat. **Pomyślnie wykonano polecenie.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Aby utworzyć nową grupę zabezpieczeń z konsoli zarządzania komputerem  
  
1.  Kliknij przycisk **Start**, kliknij przycisk **Panelu sterowania**, kliknij przycisk **narzędzia administracyjne**i kliknij przycisk **Zarządzanie komputerem** otwarcie komputera Konsola zarządzania. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może poprosić uprawnień, aby kontynuować.  
  
2.  Kliknij przycisk **Narzędzia systemowe**, kliknij przycisk **lokalnych użytkowników i grup**, kliknij prawym przyciskiem myszy **grup** folder i kliknij przycisk **Nowa grupa** w menu kontekstowym, funkcjonuje. Wpisz żądany **Nazwa grupy**, **opis** i inne szczegóły tej nowej grupy zabezpieczeń i kliknij przycisk **Utwórz** przycisk, aby utworzyć grupę zabezpieczeń.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Aby utworzyć ograniczeniami rezerwację adresu URL  
  
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij prawym przyciskiem myszy **polecenia** i kliknij przycisk **Uruchom jako Administrator** z menu kontekstowego, który pojawia się. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może poprosić uprawnień, aby kontynuować.  
  
2.  Wpisz **netsh http Dodaj adres url urlacl =http://+:80/Temporary_Listen_Addresses/ użytkownika = "\<nazwa komputera >\\< nazwa grupy zabezpieczeń\>**  w wierszu polecenia. Zastępowanie  **\<nazwa komputera >** nazwą komputera, na którym można utworzyć grupy i  **\<Nazwa grupy zabezpieczeń >** nazwą utworzoną grupę zabezpieczeń wcześniej.  
  
3.  Jeśli rezerwacja została utworzona pomyślnie, jest wyświetlany następujący komunikat. **Pomyślnie dodano rezerwację adresu URL**.
