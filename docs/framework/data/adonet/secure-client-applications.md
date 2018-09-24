---
title: Zabezpieczanie aplikacje klienckich
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: a3b035d59a39ca20f6a81fbd40d39069a7cc43c2
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2018
ms.locfileid: "46706294"
---
# <a name="secure-client-applications"></a>Zabezpieczanie aplikacje klienckich
Aplikacje składają się zazwyczaj z wielu części, które muszą być wszystkie chronione przed lukami w zabezpieczeniach, które mogą spowodować utratę danych lub w przeciwnym razie naruszyć bezpieczeństwo systemu. Tworzenie interfejsów użytkownika bezpiecznego może uniemożliwić wielu problemów przez blokowanie osoby atakujące przed uzyskaniem dostępu do danych lub zasobów systemowych.  
  
## <a name="validate-user-input"></a>Weryfikowanie danych wejściowych użytkownika  
 Podczas tworzenia aplikacji, która uzyskuje dostęp do danych, należy przyjąć, że wszystkie dane wejściowe użytkownika jest złośliwy, dopóki przeciwnego. Niewykonanie tej czynności można pozostawić aplikację na ataki. .NET Framework zawiera klasy, aby ułatwić wymuszanie domeny wartości dla kontrolki wejściowe, takie jak ograniczanie liczby znaków, które mogą być wprowadzane. Punkty zaczepienia zdarzeń umożliwiają pisanie procedur, aby sprawdzić poprawność wartości. Można sprawdzić poprawności danych wejściowych użytkownika i silnie typizowany, ograniczającej luki w aplikacji narażenia na skrypt i wstrzykiwanie kodu SQL.  
  
> [!IMPORTANT]
>  Możesz także sprawdzić poprawność danych wejściowych użytkownika w źródle danych, a także jak aplikacja kliencka. Osoba atakująca może wybrać obejścia aplikacji i ataki bezpośrednio ze źródłem danych.  
  
 [Zabezpieczenia i dane użytkownika](../../../../docs/standard/security/security-and-user-input.md)  
 W tym artykule opisano sposób obsługi błędów delikatny i potencjalnie niebezpiecznych obejmujących dane wejściowe użytkownika.  
  
 [Walidacja danych wejściowych użytkownika na stronach sieci Web platformy ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 Omówienie sprawdzania poprawności danych wejściowych za pomocą programu ASP.NET sprawdzania poprawności formantów użytkownika.  
  
 [Dane użytkownika w formularzach Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Zawiera linki i informacje dotyczące weryfikacji myszy i klawiatury w aplikacji Windows Forms.  
  
 [Wyrażeń regularnych programu .NET framework](../../../../docs/standard/base-types/regular-expressions.md)  
 Opisuje sposób używania <xref:System.Text.RegularExpressions.Regex> klasy, aby sprawdzić poprawność danych wejściowych użytkownika.  
  
## <a name="windows-applications"></a>Aplikacje Windows  
 W przeszłości aplikacje Windows są zazwyczaj uruchomione z pełnymi uprawnieniami. .NET Framework oferuje infrastrukturę, aby ograniczyć kodu wykonywanego w aplikacji Windows przy użyciu zabezpieczeń dostępu kodu (CAS). Jednak tylko urzędy certyfikacji nie wystarcza do ochrony aplikacji.  
  
 [Zabezpieczenia formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-security.md)  
 W tym artykule omówiono sposób zabezpieczania aplikacji Windows Forms i zawiera linki do powiązanych tematów.  
  
 [Formularze Windows Forms i niezarządzane aplikacje](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 W tym artykule opisano sposób interakcji z niezarządzanych aplikacji w aplikacji Windows Forms.  
  
 [Wdrożenie rozwiązania ClickOnce dla Windows Forms aplikacji](https://msdn.microsoft.com/library/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Opisuje sposób używania `ClickOnce` wdrożenia w aplikacji Windows Forms i omówiono skutki dla bezpieczeństwa.  
  
## <a name="aspnet-and-xml-web-services"></a>Program ASP.NET i usługi XML sieci Web  
 Aplikacje ASP.NET zazwyczaj trzeba ograniczyć dostęp do niektórych części witryny sieci Web i podaj inne mechanizmy ochrony danych i zabezpieczeń lokacji. Te linki zawierają przydatne informacje dotyczące zabezpieczania aplikacji ASP.NET.  
  
 Usługi sieci Web XML zawiera dane, które mogą być używane przez aplikację ASP.NET, aplikacji programu Windows Forms lub innej usługi sieci Web. Musisz zarządzać zabezpieczeniami za samą usługę sieci Web, a także zabezpieczeń w aplikacji klienckiej.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[NIB: ASP.NET Security](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d)|W tym artykule omówiono sposób zabezpieczania aplikacji ASP.NET.|  
|[Zabezpieczanie usług sieci Web XML utworzone za pomocą programu ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c)|W tym artykule omówiono sposób implementacji zabezpieczeń dla usługi sieci Web ASP.NET.|  
|[Przegląd luki w zabezpieczeniach skryptu](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|W tym artykule omówiono sposób ochrony przed atakiem wykorzystać skrypt, który próbuje wstawić złośliwego znaków do strony sieci Web.|  
|[NIB: podstawowe rozwiązania w zakresie zabezpieczeń dla aplikacji sieci Web ASP.NET](https://msdn.microsoft.com/library/94a52ab8-731d-417e-b997-721baf43df38)|Zabezpieczenia ogólne informacje i linki do dalszych dyskusji|  
  
## <a name="remoting"></a>Komunikacja zdalna  
 Wywołaniem funkcji zdalnych .NET umożliwia łatwe tworzenie aplikacji powszechnie rozproszonych, czy składniki aplikacji znajdują się już na jednym komputerze rozszerzane na całym świecie. Można tworzyć aplikacje klienta, które używają obiektów w innych procesów na tym samym komputerze lub na innym komputerze, który jest dostępny za pośrednictwem sieci. Można również użyć wywołaniem funkcji zdalnych .NET, do komunikowania się z innych domen aplikacji, w tym samym procesie.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Konfigurację zdalnego aplikacji](https://msdn.microsoft.com/library/92c0c097-d984-4315-835b-7490ecdf1097)|W tym artykule omówiono sposób konfigurowania aplikacji usług zdalnych w celu uniknięcia typowych problemów.|  
|[Zabezpieczenia w komunikacji zdalnej](https://msdn.microsoft.com/library/9574262c-d4b1-41c5-8600-24ff147c0add)|W tym artykule opisano, uwierzytelniania i szyfrowania, a także tematy dodatkowe zabezpieczenia komunikacji zdalnej.|  
|[Zabezpieczenia i zagadnienia dotyczące komunikacji zdalnej](../../../../docs/framework/misc/security-and-remoting-considerations.md)|W tym artykule opisano problemy z zabezpieczeniami, za pomocą chronionych obiektów i występujące w wielu domenach aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zalecenia dotyczące strategii dostępu do danych](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Zabezpieczanie aplikacji](/visualstudio/ide/securing-applications)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
