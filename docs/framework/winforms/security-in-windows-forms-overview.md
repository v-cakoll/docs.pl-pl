---
title: Przegląd zabezpieczeń w formularzach systemu Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57f46620e7b98bb1a4c120684075dbe065db9714
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="security-in-windows-forms-overview"></a>Przegląd zabezpieczeń w formularzach systemu Windows
Przed wydaniem [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], całego kodu uruchomiony na koncie użytkownika na komputerze ma tego samego prawa lub uprawnienia dostępu do zasobów, których użytkownik komputera zastosowano. Na przykład jeśli użytkownik uzyskał zezwolenia na dostęp do systemu plików, kod zezwolono na dostęp do systemu plików; Jeśli użytkownik uzyskał zezwolenia na dostęp do bazy danych, kod zezwolono na dostęp do tej bazy danych. Chociaż te prawa lub uprawnienia można zaakceptować dla kodu w plikach wykonywalnych, który użytkownik jawnie zainstalowany na komputerze lokalnym, nie może być możliwa do kod potencjalnie złośliwy, przesyłanych przez Internet lub lokalny Intranet. Ten kod nie powinien być uzyskiwać dostęp do zasobów komputera użytkownika bez uprawnienia.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Wprowadza infrastruktury nazywany zabezpieczeniami dostępu kodu, który umożliwia rozróżnianie uprawnienia lub prawa, które ma kod z których użytkownik ma uprawnienia. Domyślnie kod pochodzący z Internetu, jak i intranetową można uruchamiać tylko w określane jako częściowej relacji zaufania. Częściowej relacji zaufania tematy aplikacji na kilka ograniczeń: między innymi aplikacji jest ograniczony dostęp do lokalnego dysku twardego i nie można uruchomić kodu niezarządzanego. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Określa zasoby, które kod jest dozwolony dostęp do na podstawie tożsamości kodu: skąd pochodzą od tego, czy ma [zestawy Strong-Named](../../../docs/framework/app-domains/strong-named-assemblies.md), czy jest on podpisany za pomocą certyfikatu i tak dalej.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] technologii, która umożliwia wdrażanie aplikacji formularzy systemu Windows pomaga ułatwić umożliwiające tworzenie aplikacji uruchamianych w częściowej relacji zaufania, w trybie pełnego zaufania lub w częściowej relacji zaufania z podwyższonym poziomem uprawnień. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dostarcza funkcje takie jak podniesienia uprawnień i zaufanych wdrożenia aplikacji, dzięki czemu aplikacja może poprosić pełne zaufanie lub z podwyższonym poziomem uprawnień użytkownika lokalnego w sposób odpowiedzialny.  
  
## <a name="understanding-security-in-the-net-framework"></a>Opis zabezpieczeń w programie .NET Framework  
 Zabezpieczenia dostępu kodu umożliwia kod, aby być uważany za zaufany w różnym stopniu, w zależności od których pochodzą kod i na innych aspektów tożsamości kodu. Aby uzyskać więcej informacji o dowody środowisko uruchomieniowe języka wspólnego używa w celu określenia zasady zabezpieczeń, zobacz [dowód](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da). Pomaga chronić komputerów przed złośliwym kodem i pomaga chronić zaufany kod przed celowym lub przypadkowym zagrożenia dla bezpieczeństwa. Zabezpieczenia dostępu kodu również zapewnia większą kontrolę nad jakie akcje mogą wykonywać aplikacji, ponieważ można określić tylko te uprawnienia, które są potrzebne aplikacji ma. Zabezpieczenia dostępu kodu dotyczy zarządzanego kodu przeznaczonego dla środowiska CLR, nawet wtedy, gdy kod jest sprawdzenie uprawnień nie upewnij pojedynczego-zabezpieczenia dostępu kodu —. Aby uzyskać więcej informacji o zabezpieczeniach w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], zobacz [podstawowe pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md) i [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
 Jeśli użytkownik uruchomienia pliku wykonywalnego formularzy systemu Windows bezpośrednio poza serwerem sieci Web lub udziału plików, poziom zaufania przyznane aplikacji zależy którym znajduje się kod i sposobu uruchamiania. Po uruchomieniu aplikacji jest automatycznie obliczane i otrzymuje nazwany zestaw uprawnień z środowisko uruchomieniowe języka wspólnego. Domyślnie kod z komputera lokalnego jest uprawnienie Full Trust zestawu kod z sieci lokalnej otrzymuje zestaw uprawnień lokalny Intranet i kod z Internetu uzyskuje zestaw uprawnień internetowych.  
  
> [!NOTE]
>  W [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wersji 1.0 Service Pack 1 i Service Pack 2, Internet strefy Grupa kodów odbiera rób zestaw uprawnień. W innych wersjach programu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], Grupa kodów strefy Internet otrzymuje zestaw uprawnień internetowych.  
>   
>  Domyślne uprawnienia przyznane w każdym z tych zestawów uprawnienia są wymienione w [domyślnych zasad zabezpieczeń](http://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55) tematu. W zależności od uprawnień, które po otrzymaniu jego działa poprawnie lub generuje wyjątek zabezpieczeń.  
>   
>  Wiele aplikacji formularzy systemu Windows zostanie wdrożony przy użyciu [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]. Narzędzia służące do generowania [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] wdrożenia mają domyślnych zabezpieczeń inną niż co zostało wymienione powyżej. Aby uzyskać więcej informacji zobacz następujące dyskusji.  
  
 Rzeczywiste uprawnienia przyznane aplikacji może różnić się od wartości domyślnych, ponieważ zasady zabezpieczeń można modyfikować; oznacza to, że aplikacji może mieć uprawnienia na jednym komputerze, ale nie na innym.  
  
## <a name="developing-a-more-secure-windows-forms-application"></a>Tworzenie bardziej bezpieczne aplikacji Windows Forms  
 Zabezpieczenia są ważne w wszystkie kroki tworzenia aplikacji. Rozpocząć od sprawdzenia i po [Secure wytyczne kodowania](../../../docs/standard/security/secure-coding-guidelines.md).  
  
 Następnie należy zdecydować, czy uruchomić aplikację w trybie pełnego zaufania, lub czy ma być uruchamiany w częściowej relacji zaufania. Aplikacja jest uruchamiana w trybie pełnego zaufania ułatwia dostęp do zasobów na komputerze lokalnym, ale udostępnia aplikacji i jej użytkowników na wysoki zagrożenia bezpieczeństwa, jeśli nie projektowania i tworzenia aplikacji ściśle zgodnie z wytycznymi Secure kodowania temat. Aplikacja jest uruchamiana w częściowej relacji zaufania ułatwia tworzenie aplikacji bezpieczniejsze i zmniejsza ryzyko znacznie, ale wymaga więcej planowania w sposób implementowania niektórych funkcji.  
  
 Jeśli wybierzesz częściowej relacji zaufania (to znaczy albo Internet lub lokalny Intranet zestawy uprawnień) zdecydować, jak aplikacja będzie działać w tym środowisku. Formularze systemu Windows zapewnia alternatywny, bardziej bezpieczne metody implementowania funkcji w częściowo zaufanym środowisku. Niektórych części aplikacji, takich jak dostęp do danych, może być zaprojektowana i inaczej zapisywane zarówno w częściowej relacji zaufania, jak i w środowiskach pełnego zaufania. Niektóre funkcje formularzy systemu Windows, takie jak ustawienia aplikacji są przeznaczone do pracy w częściowej relacji zaufania. Aby uzyskać więcej informacji, zobacz [Przegląd ustawień aplikacji](../../../docs/framework/winforms/advanced/application-settings-overview.md).  
  
 Jeśli aplikacja wymaga więcej uprawnień niż zezwala częściowej relacji zaufania, ale nie chcesz uruchomić w trybie pełnego zaufania, można uruchomić w częściowej relacji zaufania podczas zostanie tylko te dodatkowe uprawnienia, które są potrzebne. Na przykład, jeśli chcesz uruchomić w częściowej relacji zaufania, ale należy przyznać aplikacji dostęp tylko do odczytu do katalogu w systemie plików użytkownika, możesz poprosić <xref:System.Security.Permissions.FileIOPermission> tylko dla tego katalogu. Używana poprawnie, w tym można nadać z funkcji aplikacji, zwiększyć i zminimalizować zagrożenia bezpieczeństwa użytkowników.  
  
 Podczas opracowywania aplikacji, które zostanie uruchomione w częściowej relacji zaufania, śledzić uprawnień należy uruchomić aplikację i jakie uprawnienia aplikacji można opcjonalnie użyć. Wszystkie uprawnienia są znane, należy deklaratywne żądania uprawnień na poziomie aplikacji. Żądanie uprawnienia informuje [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wykonawczego o uprawnienia, które wymaga aplikacji oraz uprawnienia, które go w szczególności nie ma. Aby uzyskać więcej informacji o uprawnieniach wysyłającego żądanie, zobacz [żąda uprawnienia](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
 Gdy użytkownik żąda uprawnienia opcjonalne, musi obsługiwać wyjątki zabezpieczeń, które mają być generowane, gdy aplikacja wykonuje akcję, która wymaga nie udzielono uprawnienia do niego. Obsługa odpowiedniego <xref:System.Security.SecurityException> zapewni, że aplikacja może kontynuować działanie. Aplikacja może używać wyjątek, aby ustalić, czy funkcja powinny stać się wyłączone dla użytkownika. Na przykład można wyłączyć aplikacji **zapisać** menu opcję, jeśli nie udzielono uprawnienia wymaganego pliku.  
  
 Czasami trudno jest wiedzieć, jeśli zostały potwierdzone wszystkie odpowiednie uprawnienia. Wywołanie metody, która wygląda nieszkodliwe na powierzchni, na przykład może uzyskać dostępu do systemu plików w pewnym momencie podczas jej wykonywania. Jeśli nie należy wdrażać aplikacji z wymaganymi uprawnieniami, jego może przetestować prawidłowo podczas debugowania go z pulpitu, ale się nie powieść po wdrożeniu. Zarówno [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] zestawu SDK i [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] narzędzia obliczania uprawnienia aplikacji musi zawierać: MT.exe polecenia odpowiednio narzędzia wiersza i obliczanie uprawnienia funkcji programu Visual Studio.  
  
 Dodatkowe funkcje zabezpieczeń formularzy systemu Windows można znaleźć w następujących tematach.  
  
|Temat|Opis|  
|-----------|-----------------|  
|-   [Plik bezpieczniejsze i dostęp do danych w formularzach systemu Windows](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)|Opisuje sposób dostępu do plików i danych w środowisku częściowej relacji zaufania.|  
|-   [Bezpieczniejsze drukowanie w formularzach systemu Windows](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)|Opisuje sposób uzyskiwać dostęp do funkcji drukowania w środowisku częściowej relacji zaufania.|  
|-   [Zagadnienia dotyczące zabezpieczeń w formularzach systemu Windows](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)|W tym artykule opisano wykonywania manipulowanie okna, korzystanie ze Schowka i wykonywania wywołań do kodu niezarządzanego w środowisku częściowej relacji zaufania.|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Wdrażanie aplikacji z odpowiednimi uprawnieniami  
 Najbardziej typowe sposób wdrażania aplikacji formularzy systemu Windows na komputerze klienckim jest z [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], technologii wdrażania, który opisuje wszystkie składniki aplikacji wymaga do uruchomienia. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] używa plików XML nazywane manifestów do opisywania pliki, które tworzą aplikacji i zestawy, a także uprawnienia aplikacji wymaga.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ma dwie technologie żądanych z podwyższonym poziomem uprawnień na komputerze klienckim. Obu tych technologii polegają na korzystanie z certyfikatów Authenticode. Certyfikaty w celu uzyskania pewności niektórych użytkowników dostarczanych przez aplikację z zaufanego źródła.  
  
 W poniższej tabeli opisano te technologie.  
  
|Technologia z podwyższonym poziomem uprawnień|Opis|  
|------------------------------------|-----------------|  
|Podniesienie uprawnień|Monituje użytkownika o zabezpieczeń oknie dialogowym po raz pierwszy uruchamia aplikację. **Podniesienia uprawnień** okno dialogowe informuje użytkownika o Wydawca aplikacji, dzięki czemu użytkownik może ona podjąć świadomej decyzji o tym, czy udzielenia zaufania|  
|Wdrażanie zaufanej aplikacji|Obejmuje administrator systemu przeprowadzania instalacji jednorazowe wydawcy Authenticode certyfikatu na komputerze klienckim. Od tego momentu wszystkie aplikacje podpisane przy użyciu certyfikatu są traktowane jako zaufane i może działać w trybie pełnego zaufania na komputerze lokalnym bez dodatkowych monitów.|  
  
 Możesz wybrać technologii będzie zależeć od środowiska wdrażania. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii wdrażania ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).  
  
 Domyślnie [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikacje wdrażane za pomocą albo program Visual Studio lub [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] narzędzia zestawu SDK (Mage.exe i MageUI.exe) są skonfigurowane do uruchomienia na komputerze klienckim, który ma pełne zaufanie. Jeśli wdrażasz aplikację przy użyciu częściowego zaufania lub przy użyciu tylko niektóre dodatkowe uprawnienia, należy zmienić to ustawienie domyślne. Można to zrobić za pomocą albo programu Visual Studio lub [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] narzędzia zestawu SDK MageUI.exe podczas konfigurowania wdrożenia. Aby uzyskać więcej informacji o sposobie używania MageUI.exe, zobacz wskazówki: Wdrażanie aplikacji ClickOnce z wiersza polecenia.  Zobacz też [porady: Ustaw uprawnienia niestandardowe dla aplikacji ClickOnce](http://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) lub [porady: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](http://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń aspektów [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] i podniesienie uprawnień, zobacz [zabezpieczanie aplikacji ClickOnce](/visualstudio/deployment/securing-clickonce-applications). Aby uzyskać więcej informacji o zaufanych wdrożenia aplikacji, zobacz [zaufane Omówienie wdrożenia aplikacji](/visualstudio/deployment/trusted-application-deployment-overview).  
  
### <a name="testing-the-application"></a>Testowanie aplikacji  
 Jeśli wdrożono aplikacji formularzy systemu Windows za pomocą programu Visual Studio, można włączyć debugowanie w częściowej relacji zaufania lub zestawu ze środowiska projektowego ograniczonych uprawnień.  Zobacz też [porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](http://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) lub [porady: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](http://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)  
 [Podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md)  
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Przegląd wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview)  
 [Mage.exe (narzędzie generowania manifestu i edytowania)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
