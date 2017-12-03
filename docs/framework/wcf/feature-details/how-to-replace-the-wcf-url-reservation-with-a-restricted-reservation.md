---
title: "Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c25403f298444732f6787979add595bd877bb2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją
Rezerwację adresu URL, można ograniczyć, kto może odbierać komunikaty z adresem URL lub zestaw adresów URL. Zastrzeżenie składa się z szablonem adresu URL, listy kontroli dostępu (ACL) i zestaw flag. Szablon adresu URL definiuje adresów URL, które zastrzeżenie ma wpływ na. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]adres URL szablony są przetwarzane, zobacz [routingu żądań przychodzących](http://go.microsoft.com/fwlink/?LinkId=136764). Listy ACL Określa, jakie użytkownik lub grupa użytkowników może odbierać komunikaty z określonych adresów URL. Flagi informujące o powodzeniu rezerwacji Aby udzielić użytkownikowi lub grupie uprawnienia do nasłuchiwania na adresie URL bezpośrednio lub Aby delegować uprawnienia do nasłuchiwania na innym procesie.  
  
 Domyślna konfiguracja systemu operacyjnego, w ramach [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tworzy zastrzeżenie globalnie dostępny za pośrednictwem portu 80, aby umożliwić wszystkim użytkownikom na uruchamianie aplikacji, które używają podwójną powiązanie HTTP do komunikacji dupleksowej. Ponieważ listy ACL na tego zastrzeżenia dla wszystkich użytkowników, administratorów nie można jawnie Zezwalaj lub nie zezwalaj uprawnienia do nasłuchiwania na adres URL lub zestaw adresów URL. W tym temacie opisano sposób usuwania tego zastrzeżenia i jak ponownie utworzyć zastrzeżenie z ograniczeniami listy ACL.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)] można wyświetlić wszystkie rezerwacji adresu URL HTTP, w wierszu polecenia z podwyższonym poziomem uprawnień, wpisując `netsh http show urlacl`.  W poniższym przykładzie pokazano, co [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powinien wyglądać rezerwację adresu URL.  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 Rezerwacja składa się z adresem URL szablon używany, gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacja używa dwóch powiązanie HTTP dla komunikacji dupleksowej. Adresy URL formularza są używane dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi do wysłania wiadomości z powrotem do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta podczas komunikacji za pośrednictwem dwóch powiązanie HTTP. Wszyscy jest uprawnienie do nasłuchiwania na adresie URL, ale nie delegować nasłuchiwanie inny proces. Ponadto listy ACL jest opisany w języku definicji deskryptora zabezpieczeń (SSDL). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Plik SSDL, zobacz [SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>Aby usunąć rezerwację adresu URL programu WCF  
  
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij prawym przyciskiem myszy **wiersza polecenia** i kliknij przycisk **Uruchom jako Administrator** menu kontekstowego, który pojawia się. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może poprosić o uprawnienia, aby kontynuować.  
  
2.  Wpisz w **http polecenia netsh, Usuń adres url urlacl = http: / / +:80/Temporary_Listen_Addresses/** w oknie wiersza polecenia.  
  
3.  Jeśli rezerwacji została usunięta pomyślnie, zostanie wyświetlony następujący komunikat. **Pomyślnie usunięto rezerwację adresu URL**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>Tworzenie nowej grupy zabezpieczeń i nową rezerwację adresu URL ograniczone  
 Aby zastąpić [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rezerwację adresu URL ograniczoną rezerwacją należy najpierw utworzyć nową grupę zabezpieczeń. Można to zrobić w jeden z dwóch sposobów: z wiersza polecenia lub w konsoli zarządzania komputerem. Wystarczy wykonać jeden.  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>Aby utworzyć nową grupę zabezpieczeń z wiersza polecenia  
  
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij prawym przyciskiem myszy **wiersza polecenia** i kliknij przycisk **Uruchom jako Administrator** menu kontekstowego, który pojawia się. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może poprosić o uprawnienia, aby kontynuować.  
  
2.  Wpisz w **net localgroup "\<Nazwa grupy zabezpieczeń >" / comment: "\<opis grupy zabezpieczeń >" / add** w wierszu polecenia. Zastępowanie  **\<Nazwa grupy zabezpieczeń >** o nazwie grupy zabezpieczeń, aby utworzyć i  **\<opis grupy zabezpieczeń >** z odpowiedniego opis Grupa zabezpieczeń.  
  
3.  Jeśli grupa zabezpieczeń został utworzony pomyślnie, zostanie wyświetlony następujący komunikat. **Polecenie zostało wykonane pomyślnie.**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>Aby utworzyć nową grupę zabezpieczeń z konsoli zarządzania komputerem  
  
1.  Kliknij przycisk **Start**, kliknij przycisk **Panelu sterowania**, kliknij przycisk **narzędzia administracyjne**i kliknij przycisk **Zarządzanie komputerem** otwarcie komputera Konsola zarządzania. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może poprosić o uprawnienia, aby kontynuować.  
  
2.  Kliknij przycisk **Narzędzia systemowe**, kliknij przycisk **lokalnych użytkowników i grup**, kliknij prawym przyciskiem myszy **grup** folder i kliknij przycisk **Nowa grupa** menu kontekstowego który pojawia się. Typ w żądaną **Nazwa grupy**, **opis** i inne szczegóły tej nowej grupy zabezpieczeń i kliknij przycisk **Utwórz** przycisk, aby utworzyć grupę zabezpieczeń.  
  
#### <a name="to-create-the-restricted-url-reservation"></a>Aby utworzyć ograniczeniami rezerwację adresu URL  
  
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, kliknij przycisk **Akcesoria**, kliknij prawym przyciskiem myszy **wiersza polecenia** i kliknij przycisk **Uruchom jako Administrator** menu kontekstowego, który pojawia się. Kliknij przycisk **Kontynuuj** w oknie Kontrola konta użytkownika (UAC), które może poprosić o uprawnienia, aby kontynuować.  
  
2.  Wpisz w **netsh http Dodaj adres url urlacl = http: / / +: 80/Temporary_Listen_Addresses/użytkownik = "\<nazwa komputera >\\< nazwa grupy zabezpieczeń\>**  w wierszu polecenia. Zastępowanie  **\<nazwa komputera >** z nazwą komputera, na którym można utworzyć grupy i  **\<Nazwa grupy zabezpieczeń >** o nazwie utworzoną grupę zabezpieczeń wcześniej.  
  
3.  Jeśli rezerwacji została utworzona pomyślnie, zostanie wyświetlony następujący komunikat. **Pomyślnie dodano rezerwację adresu URL**.
