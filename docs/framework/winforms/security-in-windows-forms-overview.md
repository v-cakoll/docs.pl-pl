---
title: Przegląd zabezpieczeń w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: 4a669b4eefeeb91c0835dc41a1c8736aacf0e14f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586648"
---
# <a name="security-in-windows-forms-overview"></a>Przegląd zabezpieczeń w formularzach systemu Windows

Przed wydaniem programu .NET Framework cały kod uruchomiony na komputerze użytkownika ma ten sam prawa lub uprawnienia dostępu do zasobów, których użytkownik komputera. Na przykład jeśli użytkownik był dozwolony dostęp do systemu plików, kod zezwolono na dostęp do systemu plików; Jeśli użytkownik zezwolono na dostęp do bazy danych, kod mógł uzyskiwać dostęp do tej bazy. Mimo że te prawa lub uprawnienia można zaakceptować dla kodu w plikach wykonywalnych, który użytkownik jawnie zainstalowany na komputerze lokalnym, nie może być możliwa do kod potencjalnie złośliwy, pochodzące z Internetu lub lokalny Intranet. Ten kod nie należy uzyskiwać dostęp do zasobów komputera użytkownika bez uprawnień.

.NET Framework wprowadza infrastruktura zabezpieczeń dostępu kodu, która umożliwia odróżnienie uprawnienia lub prawa, które kod ma z prawa, które użytkownik ma. Domyślnie kod pochodzący z sieci Internet, jak i intranetową można uruchamiać tylko w określane jako częściowej relacji zaufania. Częściowej relacji zaufania przedmioty aplikacji szereg ograniczeń: między innymi, aplikacja jest ograniczony dostęp do lokalnego dysku twardego i nie można uruchomić kod niezarządzany. .NET Framework określa zasoby, które kod może być dostępu na podstawie tożsamości ten kod: jego pochodzenie, czy ma [zestawy Strong-Named](../app-domains/strong-named-assemblies.md)na to, czy jest on podpisany za pomocą certyfikatu i tak dalej.

[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] technologii, która umożliwia wdrażanie aplikacji Windows Forms, pomaga ułatwiają tworzenie aplikacji działających w częściowej relacji zaufania, w trybie pełnego zaufania lub w częściowej relacji zaufania z podwyższonym poziomem uprawnień. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dostarcza funkcje takie jak podniesienie uprawnień i wdrażanie zaufanych aplikacji, dzięki czemu aplikacja poprosić pełnego zaufania lub z podwyższonym poziomem uprawnień użytkownika lokalnego w odpowiedzialny sposób.

## <a name="understanding-security-in-the-net-framework"></a>Opis zabezpieczeń w programie .NET Framework

Zabezpieczenia dostępu kodu umożliwia kodu być uważany za zaufany w różnym stopniu, w zależności od tego, gdzie kod pochodzi, a także na innych aspektów tożsamości kodu. Aby uzyskać więcej informacji na temat dowód, używa środowiska uruchomieniowego języka wspólnego, aby określić zasady zabezpieczeń, zobacz [dowód](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)). Pomaga chronić systemy komputerowe przed złośliwym kodem i pomaga chronić zaufanego kodu przed celowo lub przypadkowo zagrożenia dla bezpieczeństwa. Zabezpieczenia dostępu kodu oferuje również większą kontrolę nad jakie akcje mogą wykonywać aplikacji, ponieważ można określić tylko uprawnienia należy aplikacja. Zabezpieczenia dostępu kodu ma wpływ na całego zarządzanego kodu, który jest przeznaczony dla środowiska CLR, nawet wtedy, gdy kod jest nie upewnij pojedynczego — zabezpieczenia dostępu kodu — sprawdzenie uprawnień. Aby uzyskać więcej informacji na temat zabezpieczeń w programie .NET Framework, zobacz [podstawowe pojęcia dotyczące zabezpieczeń](../../standard/security/key-security-concepts.md) i [podstawy zabezpieczeń dostępu kodu](../misc/code-access-security-basics.md).

Jeśli użytkownik uruchomienia pliku wykonywalnego formularze Windows bezpośrednio zniżki w stosunku do serwera sieci Web lub udziału plików, stopień zaufania udzielenie aplikacji zależy od zawierającej kod i sposób jej ponownym uruchomieniu. Po uruchomieniu aplikacji, automatycznie jest obliczane i odbierze nazwany zestaw uprawnień ze środowiska uruchomieniowego języka wspólnego. Domyślnie kod z komputera lokalnego jest udzielane uprawnienie Full Trust ustawiona, kod z sieci lokalnej ma udzielone zestaw uprawnień lokalny Intranet i kod z Internetu uzyskuje Internet zestaw uprawnień.

> [!NOTE]
> W .NET Framework w wersji 1.0 Service Pack 1 i Service Pack 2, Internet strefa kodu Grupa otrzymuje rób zestaw uprawnień. We wszystkich innych wersjach programu .NET Framework grupy kodu strefy Internet odbiera Internet zestaw uprawnień.
>
> Domyślne uprawnienia przyznane w każdym z tych zestawów uprawnień są wymienione w [domyślnych zasad zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100)) tematu. W zależności od uprawnień, które aplikacja otrzyma jest działa poprawnie lub generuje wyjątek zabezpieczeń.
>
> Będzie można wdrożyć wiele aplikacji Windows Forms przy użyciu [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]. Narzędzia służące do generowania [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] wdrożenia ma ustawienia domyślne zabezpieczeń inną niż co została omówiony wcześniej. Aby uzyskać więcej informacji zobacz następujące dyskusji.

Rzeczywiste uprawnienia przyznane aplikacji może różnić się od wartości domyślnych, ponieważ zasady zabezpieczeń można zmodyfikować; to oznacza, że aplikacja może mieć uprawnień na jednym komputerze, ale nie na innym.

## <a name="developing-a-more-secure-windows-forms-application"></a>Tworzenie bardziej bezpieczną aplikację formularzy Windows

Zabezpieczenia są ważne dla wszystkich kroków tworzenia aplikacji. Rozpocznij od przeglądania i postępowanie [Secure wytycznych kodowania](../../standard/security/secure-coding-guidelines.md).

Następnie należy zdecydować, czy uruchomić aplikację w trybie pełnego zaufania lub tego, czy ma być uruchamiany w częściowej relacji zaufania. Aplikacja jest uruchamiana w trybie pełnego zaufania, ułatwia dostęp do zasobów na komputerze lokalnym, ale udostępnia aplikacji i jej użytkownikach, na wysokie ryzyko naruszenia zabezpieczeń, jeśli nie projektowania i tworzenia aplikacji wyłącznie zgodnie z wytycznymi bezpiecznego kodowania temat. Aplikacja jest uruchamiana w trybie częściowego zaufania sprawia, że łatwiej tworzyć bardziej bezpiecznych aplikacji i zmniejsza dużo ryzyka, ale wymaga więcej planowania w sposób wdrażania niektórych funkcji.

Jeśli wybierzesz opcję częściowej relacji zaufania (czyli albo Internet lub lokalny Intranet zestawy uprawnień), zdecydować, jak Twoja aplikacja działa w tym środowisku. Windows Forms zapewnia alternatywne, bardziej bezpiecznymi sposobów implementowania funkcji w częściowo zaufanym środowisku. Niektórych części aplikacji, takich jak dostęp do danych, może być zaprojektowane i inaczej napisana dla zarówno w częściowej relacji zaufania, jak i w środowiskach pełnego zaufania. Niektóre funkcje Windows Forms, takie jak ustawienia aplikacji są przeznaczone do pracy w trybie częściowego zaufania. Aby uzyskać więcej informacji, zobacz [Przegląd ustawień aplikacji](./advanced/application-settings-overview.md).

Jeśli Twoja aplikacja potrzebuje więcej uprawnień niż pozwala częściowej relacji zaufania, ale nie chcesz uruchomić w trybie pełnego zaufania, można uruchomić w częściowej relacji zaufania podczas potwierdzające tylko te dodatkowe uprawnienia, których potrzebujesz. Na przykład, jeśli mają być uruchamiane w częściowej relacji zaufania, ale musisz przyznać aplikacji dostęp tylko do odczytu do katalogu w systemie plików użytkownika, możesz poprosić o <xref:System.Security.Permissions.FileIOPermission> tylko dla tego katalogu. Prawidłowo wykorzystywane tej metody można nadać funkcjonalność swojej aplikacji, zwiększyć i zminimalizować zagrożenia bezpieczeństwa dla użytkowników.

Podczas opracowywania aplikacji, która jest uruchamiana w częściowej relacji zaufania, śledzić jakie uprawnienia należy uruchomić aplikację i jakie uprawnienia można opcjonalnie używać aplikacja. Wszystkie uprawnienia są znane, należy deklaratywne żądania o uprawnienia na poziomie aplikacji. Żądanie uprawnień informuje wykonawczego o uprawnienia, które Twoja aplikacja potrzebuje i uprawnienia, które je specjalnie nie ma w programie .NET Framework. Aby uzyskać więcej informacji na temat żądania uprawnień, zobacz [żąda uprawnienia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).

Opcjonalne uprawnienia w przypadku żądania, musi obsługiwać wyjątki zabezpieczeń, które mają być generowane, gdy aplikacja wykonuje akcję, która wymaga uprawnienia nie udzielone. Odpowiednie, obsługa <xref:System.Security.SecurityException> zapewni, że aplikacja może w dalszym ciągu działać. Aplikacja może używać wyjątek, aby ustalić, czy funkcja powinna stać się wyłączony dla użytkownika. Na przykład można wyłączyć aplikacji **Zapisz** opcję menu, jeśli nie zostało udzielone uprawnienie wymaganego pliku.

Czasami trudno jest znać, jeśli zostały potwierdzone odpowiednie uprawnienia. Wywołanie metody, która wygląda nieszkodliwe na powierzchni na przykład, mogą uzyskiwać dostęp do systemu plików w pewnym momencie podczas jego wykonywania. Jeśli nie należy wdrażać aplikacji przy użyciu wszystkich wymaganych uprawnień, jego może przetestować prawidłowo podczas jej debugowania na komputerze, ale się nie powieść podczas wdrażania. Zarówno [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] zestawu SDK i programu Visual Studio 2005 zawiera narzędzia do obliczania uprawnienia, aplikacja musi: MT.exe polecenia narzędzia wiersza i funkcja Obliczanie uprawnień programu Visual Studio, odpowiednio.

W poniższych tematach opisano dodatkowe funkcje zabezpieczeń Windows Forms.

|Temat|Opis|
|-----------|-----------------|
|- [Większe bezpieczeństwo plików i dostęp do danych w formularzach Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)|Opisuje sposób dostępu do plików i danych w środowisku częściowej relacji zaufania.|
|- [Bezpieczniejsze drukowanie w formularzach Windows Forms](more-secure-printing-in-windows-forms.md)|Zawiera opis sposobu uzyskania dostępu do funkcji drukowania w środowisku częściowej relacji zaufania.|
|- [Zagadnienia dotyczące dodatkowych zabezpieczeń w formularzach Windows Forms](additional-security-considerations-in-windows-forms.md)|W tym artykule opisano przeprowadzanie manipulacji okna: Korzystanie ze Schowka i wykonywania wywołań do kodu niezarządzanego w środowisku częściowej relacji zaufania.|

### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Wdrażanie aplikacji z odpowiednimi uprawnieniami

Najbardziej typowe sposób wdrażania aplikacji Windows Forms, komputer kliencki jest [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], to technologia wdrażania, który opisuje wszystkie składniki Twoja aplikacja potrzebuje do uruchomienia. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] używa plików XML o nazwie manifesty do opisania zestawów i plików, wchodzące w skład aplikacji, a także uprawnienia aplikacji wymaga.

[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ma dwie technologie do żądania z podwyższonym poziomem uprawnień na komputerze klienckim. Obie technologie opierają się na korzystanie z certyfikatów Authenticode. Certyfikaty w celu uzyskania niektóre pewności użytkowników, które aplikacja ma pochodzą z zaufanego źródła.

W poniższej tabeli opisano te technologie.

|Technologia podwyższonym poziomem uprawnień|Opis|
|------------------------------------|-----------------|
|Podniesienie uprawnień|Monituje użytkownika o bezpieczeństwo okna dialogowego po raz pierwszy do uruchamiania aplikacji. **Podnoszenia poziomu uprawnień** okno dialogowe informuje użytkownika o Wydawca aplikacji, tak aby użytkownik może podjąć świadomą decyzję o tym, czy udzielenia zaufania|
|Wdrażanie zaufanej aplikacji|Wiąże się z administratorem systemu, przeprowadzania instalacji jednorazowe wydawcy Authenticode certyfikatu na komputerze klienckim. Od tego momentu wszystkie aplikacje podpisane przy użyciu certyfikatu są traktowane jako zaufane i można uruchomić w trybie pełnego zaufania na komputerze lokalnym, bez dodatkowych monitów.|

Możesz wybrać technologie będzie zależeć od środowiska wdrażania. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii wdrażania ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).

Domyślnie [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikacje wdrożone za pomocą programu Visual Studio lub [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] narzędzi zestawu SDK (Mage.exe i MageUI.exe) są skonfigurowane do uruchamiania na komputerze klienckim, który ma pełne zaufanie. Jeśli aplikacja jest wdrażana za niektóre dodatkowe uprawnienia lub za pomocą częściowej relacji zaufania, należy zmienić to ustawienie domyślne. Można to zrobić za pomocą programu Visual Studio lub [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] zestawu SDK narzędzia MageUI.exe, podczas konfigurowania wdrożenia. Aby uzyskać więcej informacji na temat sposobu użycia programu MageUI.exe, zobacz Przewodnik po: Wdrażanie aplikacji ClickOnce z wiersza polecenia.  Zobacz też [jak: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hafybdaa(v=vs.110)) lub [jak: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application).

Aby uzyskać więcej informacji na temat zabezpieczeń aspektów [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] i podnoszenia poziomu uprawnień, zobacz [zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications). Aby uzyskać więcej informacji na temat zaufanego wdrożenia aplikacji, zobacz [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).

### <a name="testing-the-application"></a>Testowanie aplikacji

Jeśli wdrożono aplikację Windows Forms przy użyciu programu Visual Studio, możesz włączyć debugowanie w częściowej relacji zaufania lub z ograniczonym zestawem uprawnień ze środowiska projektowego.  Zobacz też [jak: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions).

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia formularzy Windows Forms](windows-forms-security.md)
- [Podstawy zabezpieczeń dostępu kodu](../misc/code-access-security-basics.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przegląd wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
