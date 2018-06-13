---
title: Zabezpieczanie aplikacji klienckich
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: ac4f1c3debacd89a0763aa8f30de3c5463c5d24d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361562"
---
# <a name="secure-client-applications"></a>Zabezpieczanie aplikacji klienckich
Aplikacje zwykle składają się z wielu części, które muszą być wszystkie chronione przed lukami w zabezpieczeniach, które mogą spowodować utratę danych lub naruszyć bezpieczeństwo systemu, w przeciwnym razie wartość. Tworzenie interfejsów bezpiecznego użytkownika może uniemożliwić wiele problemów blokując osoby atakujące przed uzyskaniem dostępu do danych albo zasobów systemowych.  
  
## <a name="validate-user-input"></a>Sprawdzanie poprawności danych wejściowych użytkownika  
 Podczas tworzenia aplikacji, która uzyskuje dostęp do danych, użytkownik powinien przyjęto założenie, że wszystkie dane wejściowe użytkownika jest złośliwe, dopóki przeciwnego. Błąd w tym celu można pozostawić aplikacji narażony na ataki. .NET Framework zawiera klasy, aby wymusić domeny wartościami dla kontrolki wejściowe, takie jak ograniczenie liczby znaków, które można wprowadzić. Punkty zaczepienia zdarzeń pozwalają na zapis procedury, aby sprawdzić poprawność wartości. Można sprawdzić poprawności danych wejściowych użytkownika i silnie typizowany, ograniczającej wykorzystuje aplikacji zagrożeń do skryptu i iniekcja kodu SQL.  
  
> [!IMPORTANT]
>  Należy także sprawdzić dane wejściowe użytkownika w źródle danych, a także jak aplikacja kliencka. Osoba atakująca może dołączyć do obejścia aplikacji i ataki bezpośrednio ze źródłem danych.  
  
 [Zabezpieczenia i dane użytkownika](../../../../docs/standard/security/security-and-user-input.md)  
 Opisuje sposób obsługi błędów delikatny i potencjalnie niebezpiecznych obejmujących dane wejściowe użytkownika.  
  
 [Walidacja danych wejściowych użytkownika na stronach sieci Web ASP.NET](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 Omówienie sprawdzania poprawności z użytkownikiem za pomocą formantów weryfikacji platformy ASP.NET.  
  
 [Dane użytkownika w formularzach Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Zawiera łącza i informacje dotyczące sprawdzania poprawności myszy i klawiatury w aplikacjach formularzy systemu Windows.  
  
 [.NET framework — nieprawidłowe wyrażenia](../../../../docs/standard/base-types/regular-expressions.md)  
 Informacje dotyczące używania <xref:System.Text.RegularExpressions.Regex> klasy sprawdzania poprawności danych wejściowych użytkownika.  
  
## <a name="windows-applications"></a>Aplikacje systemu Windows  
 W przeszłości aplikacji systemu Windows, zazwyczaj uruchamiane z pełnymi uprawnieniami. .NET Framework zapewnia infrastrukturę do ograniczenia kodu wykonywanego w aplikacji systemu Windows przy użyciu zabezpieczeń dostępu kodu (CAS). Jednak tylko urzędy certyfikacji nie jest wystarczająco do ochrony aplikacji.  
  
 [Zabezpieczenia formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-security.md)  
 Zawiera omówienie zabezpieczania aplikacji formularzy systemu Windows, a także linki do powiązanych tematów.  
  
 [Formularze Windows Forms i niezarządzane aplikacje](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Opisuje sposób interakcji z niezarządzanych aplikacji w aplikacji formularzy systemu Windows.  
  
 [Wdrożenie ClickOnce dla systemu Windows formularzy aplikacji](http://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Informacje dotyczące używania `ClickOnce` wdrożenia w aplikacji formularzy systemu Windows i omówiono wpływ na zabezpieczenia.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET i usługi sieci Web XML  
 Aplikacje ASP.NET zazwyczaj konieczne ograniczanie dostępu do niektórych części witryny sieci Web i podaj inne mechanizmy ochrony danych i zabezpieczeń lokacji. Te linki udostępniają przydatne informacje dotyczące zabezpieczania aplikacji ASP.NET.  
  
 Usługi XML sieci Web zawiera dane, które mogą być używane przez aplikację ASP.NET, aplikacji formularzy systemu Windows lub innej usługi sieci Web. Trzeba zarządzać zabezpieczeń dla usługi sieci Web, sam, jak również zabezpieczeń dla aplikacji klienckich.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[NIB: ASP.NET Security](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d)|W tym artykule omówiono zabezpieczania aplikacji ASP.NET.|  
|[Zabezpieczanie usług XML sieci Web utworzony za pomocą programu ASP.NET](http://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c)|Zawiera omówienie sposobu implementacji zabezpieczeń dla usługi sieci Web ASP.NET.|  
|[Przegląd luki w zabezpieczeniach skryptu](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|W tym artykule omówiono sposób w celu ochrony przed atakiem wykorzystać skrypt, który próbuje wstawić znaki złośliwego do strony sieci Web.|  
|[NIB: podstawowe wskazówki dotyczące zabezpieczeń dla aplikacji sieci Web ASP.NET](http://msdn.microsoft.com/library/94a52ab8-731d-417e-b997-721baf43df38)|Informacje ogólne zabezpieczeń i linki do dalszych dyskusji|  
  
## <a name="remoting"></a>Usługi zdalne  
 Funkcji zdalnych .NET umożliwia łatwe tworzenie dystrybucji aplikacji, czy składniki aplikacji znajdują się już na jednym komputerze lub rozszerzane na całym świecie. Można tworzyć aplikacje klienckie używające obiektów w innych procesów na tym samym komputerze lub na innym komputerze, który jest dostępny za pośrednictwem sieci. Umożliwia także .NET remoting do komunikowania się z innymi domenami aplikacji, w tym samym procesie.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Konfiguracja aplikacji zdalnego](http://msdn.microsoft.com/library/92c0c097-d984-4315-835b-7490ecdf1097)|W tym artykule omówiono sposób konfigurowania aplikacji usług zdalnych w celu uniknięcia typowych problemów.|  
|[Zabezpieczenia w zdalnych](http://msdn.microsoft.com/library/9574262c-d4b1-41c5-8600-24ff147c0add)|Opisuje, uwierzytelniania i szyfrowania, a także tematy dodatkowe zabezpieczenia komunikacji zdalnej.|  
|[Bezpieczeństwo i uwagi dotyczące komunikacji zdalnej](../../../../docs/framework/misc/security-and-remoting-considerations.md)|W tym artykule opisano problemy dotyczące zabezpieczeń obiektach chronionych i przecięcia domeny aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zalecenia dotyczące strategii dostępu do danych](http://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Zabezpieczanie aplikacji](/visualstudio/ide/securing-applications)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
