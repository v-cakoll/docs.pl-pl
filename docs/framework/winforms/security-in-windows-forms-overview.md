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
ms.openlocfilehash: 08c80eccee395d9141978a7d4594205af1a51ed9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972131"
---
# <a name="security-in-windows-forms-overview"></a>Przegląd zabezpieczeń w formularzach systemu Windows

Przed wydaniem .NET Framework cały kod uruchomiony na komputerze użytkownika miał te same prawa lub uprawnienia, aby uzyskać dostęp do zasobów, które miały użytkownik komputera. Na przykład, jeśli Użytkownik zezwolił na dostęp do systemu plików, kod miał zezwolenie na dostęp do systemu plików; Jeśli Użytkownik zezwolił na dostęp do bazy danych, może uzyskać dostęp do tej bazy danych. Chociaż te prawa i uprawnienia mogą być akceptowalne dla kodu w plikach wykonywalnych, które użytkownik jawnie zainstalował na komputerze lokalnym, mogą nie być akceptowalne dla potencjalnie złośliwego kodu pochodzącego z Internetu lub lokalnego intranetu. Ten kod nie powinien być w stanie uzyskać dostępu do zasobów komputera użytkownika bez uprawnień.

W .NET Framework wprowadzono infrastrukturę o nazwie zabezpieczenia dostępu kodu, która umożliwia odróżnienie uprawnień lub praw do tego kodu od praw, które użytkownik ma. Domyślnie kod pochodzący z Internetu i intranetu można uruchomić tylko w tym, co jest znane jako częściowe zaufanie. Częściowo ufają podmiotom, które są aplikacjami z serii ograniczeń: między innymi, aplikacja ma ograniczone dostęp do lokalnego dysku twardego i nie może uruchamiać kodu niezarządzanego. .NET Framework kontroluje zasoby, do których kod może uzyskać dostęp na podstawie tożsamości tego kodu: skąd pochodzi, czy ma [zestawy o silnych nazwach](../../standard/assembly/strong-named.md), niezależnie od tego, czy są podpisane za pomocą certyfikatu itd.

Technologia ClickOnce, która służy do wdrażania aplikacji Windows Forms, ułatwia tworzenie aplikacji, które działają w częściowej relacji zaufania, w pełnym zaufaniu lub w częściowej relacji zaufania z podwyższonym poziomem uprawnień. Technologia ClickOnce udostępnia funkcje takie jak podniesienie uprawnień i zaufane aplikacje, dzięki czemu aplikacja może wymagać pełnego zaufania lub podwyższonego poziomu uprawnień użytkownika lokalnego w odpowiedzialny sposób.

## <a name="understanding-security-in-the-net-framework"></a>Informacje o zabezpieczeniach w .NET Framework

Zabezpieczenia dostępu kodu umożliwiają ufanie kodowi różnym stopom, w zależności od tego, gdzie pochodzą z kodu, oraz od innych aspektów tożsamości kodu. Aby uzyskać więcej informacji na temat dowodów, które są używane przez środowisko uruchomieniowe języka wspólnego do określania zasad zabezpieczeń, zobacz [dowody](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)). Pomaga chronić systemy komputerowe przed złośliwym kodem i pomaga chronić zaufany kod przed celowo lub przypadkowo z naruszeniem zabezpieczeń. Zabezpieczenia dostępu kodu oferują również większą kontrolę nad tym, jakie akcje może wykonać aplikacja, ponieważ można określić tylko te uprawnienia, które mają być używane w aplikacji. Zabezpieczenia dostępu kodu mają wpływ na cały kod zarządzany, który jest przeznaczony dla środowiska uruchomieniowego języka wspólnego, nawet jeśli ten kod nie powoduje sprawdzenia uprawnień dostępu jednokodowego do zabezpieczeń. Aby uzyskać więcej informacji o zabezpieczeniach w .NET Framework, zobacz podstawowe [pojęcia dotyczące zabezpieczeń](../../standard/security/key-security-concepts.md) i [zabezpieczenia dostępu kodu](../misc/code-access-security-basics.md).

Jeśli użytkownik uruchamia Windows Forms plik wykonywalny bezpośrednio z serwera sieci Web lub udziału plików, stopień zaufania przyznany aplikacji zależy od miejsca, w którym znajduje się kod, oraz sposobu jego uruchomienia. Gdy aplikacja jest uruchomiona, zostanie ona automatycznie oceniona i otrzyma nazwany zestaw uprawnień z aparatu plików wykonywalnych języka wspólnego. Domyślnie kod z komputera lokalnego ma przyznane uprawnienia pełnego zaufania, kod z sieci lokalnej otrzymuje zestaw uprawnień Lokalny intranet, a kod z Internetu otrzymuje zestaw uprawnień internetowych.

> [!NOTE]
> W .NET Framework w wersji 1,0 z dodatkiem Service Pack 1 i Service Pack 2, grupa kodów strefy Internet odbierze zestaw uprawnień Nothing. We wszystkich innych wersjach .NET Framework Grupa kod strefy internetowej odbiera zestaw uprawnień internetowych.
>
> Domyślne uprawnienia przyznane w każdym z tych zestawów uprawnień są wymienione w temacie [domyślne zasady zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100)) . W zależności od uprawnień otrzymywanych przez aplikację działa prawidłowo lub generuje wyjątek zabezpieczeń.
>
> Wiele aplikacji Windows Forms zostanie wdrożonych przy użyciu technologii ClickOnce. Narzędzia używane do generowania wdrożenia ClickOnce mają różne wartości domyślne zabezpieczeń niż te, które zostały omówione wcześniej. Więcej informacji można znaleźć w poniższej dyskusji.

Rzeczywiste uprawnienia przyznane aplikacji mogą różnić się od wartości domyślnych, ponieważ zasady zabezpieczeń można modyfikować. oznacza to, że aplikacja może mieć uprawnienia na jednym komputerze, ale nie na innym.

## <a name="developing-a-more-secure-windows-forms-application"></a>Tworzenie bezpieczniejszej aplikacji Windows Forms

Zabezpieczenia są ważne we wszystkich krokach tworzenia aplikacji. Zacznij od przejrzenia i postępując zgodnie ze [wskazówkami dotyczącymi bezpiecznego kodowania](../../standard/security/secure-coding-guidelines.md).

Następnie zdecyduj, czy aplikacja musi działać w trybie pełnego zaufania, czy ma być uruchamiana w częściowej relacji zaufania. Uruchamianie aplikacji w trybie pełnego zaufania ułatwia uzyskiwanie dostępu do zasobów na komputerze lokalnym, ale udostępnia swoją aplikację i jej użytkownikom wysoki poziom ryzyka związanego z bezpieczeństwem, jeśli nie projektujesz i nie opracowujesz aplikacji wyłącznie zgodnie z zasadami bezpiecznego kodowania rozdziału. Uruchamianie aplikacji w częściowej relacji zaufania ułatwia tworzenie bezpieczniejszej aplikacji i zmniejsza ryzyko, ale wymaga większego planowania w przypadku implementacji niektórych funkcji.

W przypadku wybrania opcji częściowej relacji zaufania (czyli Internetu lub lokalnych zestawów uprawnień) Zdecyduj, jak aplikacja ma działać w tym środowisku. Windows Forms oferuje alternatywne, bardziej bezpieczne sposoby implementowania funkcji w środowisku częściowo zaufanym. Niektóre części aplikacji, takie jak dostęp do danych, można zaprojektować i napisać inaczej w przypadku środowisk częściowej relacji zaufania i pełnego zaufania. Niektóre funkcje Windows Forms, takie jak ustawienia aplikacji, są przeznaczone do pracy w częściowej relacji zaufania. Aby uzyskać więcej informacji, zobacz [Omówienie ustawień aplikacji](./advanced/application-settings-overview.md).

Jeśli aplikacja wymaga więcej uprawnień niż zezwala częściowa relacja zaufania, ale nie chcesz uruchamiać w trybie pełnego zaufania, możesz uruchomić w częściowej relacji zaufania przy zapewnieniu tylko potrzebnych dodatkowych uprawnień. Na przykład, jeśli chcesz uruchomić w częściowej relacji zaufania, ale musisz udzielić aplikacji dostępu tylko do odczytu do katalogu w systemie plików użytkownika, możesz poprosić <xref:System.Security.Permissions.FileIOPermission> tylko o ten katalog. Ta metoda jest używana prawidłowo, ale takie podejście może zwiększyć funkcjonalność aplikacji i zminimalizować zagrożenie bezpieczeństwa dla użytkowników.

Podczas tworzenia aplikacji, która będzie uruchamiana w częściowej relacji zaufania, śledź uprawnienia, które aplikacja musi uruchomić, oraz uprawnienia, które mogą być używane przez aplikację. Jeśli wszystkie uprawnienia są znane, należy wykonać żądanie deklaratywne dla uprawnienia na poziomie aplikacji. Żądanie uprawnień informuje .NET Framework czasie uruchamiania o tym, które uprawnienia są wymagane przez aplikację i które z nich nie ma. Aby uzyskać więcej informacji na temat żądania uprawnień, zobacz [żądanie uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).

W przypadku żądania uprawnień opcjonalnych należy obsługiwać wyjątki zabezpieczeń, które zostaną wygenerowane, jeśli aplikacja wykonuje akcję, która wymaga uprawnień, które nie zostały do niego przyznane. Odpowiednia obsługa <xref:System.Security.SecurityException> zapewnia, że aplikacja będzie mogła nadal działać. Aplikacja może użyć wyjątku, aby określić, czy funkcja powinna zostać wyłączona dla użytkownika. Na przykład aplikacja może wyłączyć opcję menu **Zapisz** , jeśli nie udzielono uprawnienia wymaganego pliku.

Czasami trudno jest wiedzieć, czy zostały potwierdzone wszystkie odpowiednie uprawnienia. Wywołanie metody, które wyszukuje niewielkiej ilości na powierzchni, na przykład może uzyskać dostęp do systemu plików w pewnym momencie podczas jego wykonywania. Jeśli aplikacja nie zostanie wdrożona ze wszystkimi wymaganymi uprawnieniami, może ona być testowana w przypadku debugowania na pulpicie, ale podczas wdrażania nie powiedzie się. Zarówno zestaw .NET Framework 2,0 SDK, jak i Visual Studio 2005 zawierają narzędzia do obliczania uprawnień wymaganych przez aplikację: narzędzia wiersza polecenia MT. exe i funkcji Oblicz uprawnienia w programie Visual Studio.

W poniższych tematach opisano dodatkowe funkcje zabezpieczeń Windows Forms.

|Temat|Opis|
|-----------|-----------------|
|- [Bezpieczniejszy dostęp do plików i danych w Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)|Opisuje sposób uzyskiwania dostępu do plików i danych w środowisku częściowej relacji zaufania.|
|- [Bezpieczniejsze drukowanie w Windows Forms](more-secure-printing-in-windows-forms.md)|Opisuje sposób uzyskiwania dostępu do funkcji drukowania w środowisku częściowej relacji zaufania.|
|- [Dodatkowe zagadnienia dotyczące zabezpieczeń w Windows Forms](additional-security-considerations-in-windows-forms.md)|Opisuje wykonywanie manipulowania oknem przy użyciu Schowka i wykonywanie wywołań do kodu niezarządzanego w środowisku częściowej relacji zaufania.|

### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Wdrażanie aplikacji z odpowiednimi uprawnieniami

Najczęstszym sposobem wdrażania aplikacji Windows Forms na komputerze klienckim jest technologia ClickOnce, która opisuje wszystkie składniki wymagane do uruchomienia aplikacji. ClickOnce używa plików XML o nazwie Manifests do opisywania zestawów i plików, które składają się na aplikację, a także uprawnień wymaganych przez aplikację.

Technologia ClickOnce ma dwie technologie żądające podniesionych uprawnień na komputerze klienckim. Obie technologie korzystają z certyfikatów Authenticode. Certyfikaty zapewniają pewne gwarancje użytkownikom, że aplikacja pochodzi z zaufanego źródła.

W poniższej tabeli opisano te technologie.

|Podwyższona technologia uprawnień|Opis|
|------------------------------------|-----------------|
|Podniesienie uprawnień|Po pierwszym uruchomieniu aplikacji pojawia się okno dialogowe z zabezpieczeniami. Okno dialogowe **podniesienia uprawnień** informuje użytkownika o tym, kto opublikował aplikację, dzięki czemu użytkownik może podejmować świadomą decyzję o tym, czy udzielić mu dodatkowego zaufania|
|Wdrożenie zaufanej aplikacji|Obejmuje administrator systemu wykonujący jednorazową instalację certyfikatu Authenticode wydawcy na komputerze klienckim. Od tego momentu wszystkie aplikacje podpisane przy użyciu certyfikatu są uznawane za zaufane i mogą być uruchamiane z pełnym zaufaniem na komputerze lokalnym bez dodatkowych monitów.|

Wybrana Technologia będzie zależeć od środowiska wdrażania. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii wdrażania ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).

Domyślnie aplikacje ClickOnce wdrożone przy użyciu programu Visual Studio lub narzędzi zestawu .NET Framework SDK (Mage. exe i MageUI. exe) są skonfigurowane do uruchamiania na komputerze klienckim, który ma pełne zaufanie. W przypadku wdrażania aplikacji przy użyciu częściowej relacji zaufania lub korzystania tylko z dodatkowych uprawnień należy zmienić to ustawienie domyślne. Można to zrobić za pomocą programu Visual Studio lub narzędzia .NET Framework SDK MageUI. exe podczas konfigurowania wdrożenia. Aby uzyskać więcej informacji o sposobach korzystania z programu MageUI. [exe, zobacz Przewodnik: Ręczne wdrażanie aplikacji](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)ClickOnce.  Zapoznaj [się również z tematem: Ustawianie uprawnień niestandardowych dla aplikacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hafybdaa(v=vs.110)) ClickOnce lub [instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji](/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application)ClickOnce.

Aby uzyskać więcej informacji na temat aspektów zabezpieczeń ClickOnce i podniesienia uprawnień, zobacz [Zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications). Aby uzyskać więcej informacji na temat wdrażania zaufanych aplikacji, zobacz [Omówienie wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview).

### <a name="testing-the-application"></a>Testowanie aplikacji

Jeśli aplikacja Windows Forms została wdrożona za pomocą programu Visual Studio, można włączyć debugowanie w częściowej relacji zaufania lub z ograniczonym zestawem uprawnień ze środowiska deweloperskiego.  Zapoznaj [się również z tematem: Debuguj aplikację ClickOnce z ograniczonymi uprawnieniami](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions).

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia formularzy Windows Forms](windows-forms-security.md)
- [Podstawowe informacje o zabezpieczeniach dostępu kodu](../misc/code-access-security-basics.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przegląd wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
