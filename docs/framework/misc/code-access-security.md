---
title: "Zabezpieczenia dostępu kodu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- named permission sets, code access security
- call stacks
- malicious code
- stack walk
- security [.NET Framework], code access security
- permissions [.NET Framework], code access security
- trusted code
- mobile code security
- unmanaged code, code access security
- granting permissions, code access security
- user authentication, code access security
- code access security
ms.assetid: 859af632-c80d-4736-8d6f-1e01b09ce127
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3582516dece69589d98acb66f1dde2249d9d8832
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="code-access-security"></a>Zabezpieczenia dostępu kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Systemów komputerowych wysokim stopniu połączenia współczesnych często są widoczne dla kodu pochodzącego z różnymi, prawdopodobnie nieznane źródła. Kod można dołączyć do wiadomości e-mail, zawartych w dokumentach lub pobrane za pośrednictwem Internetu. Niestety w przypadku wielu użytkowników komputera wystąpił firsthand skutków złośliwego kodu przenośnych, w tym wirusy lub robaki, które mogą uszkodzenia lub zniszczenia danych i kosztów czas i pieniądze.  
  
 Najbardziej typowych mechanizmów zabezpieczeń udzielić uprawnień do użytkowników na podstawie ich poświadczeń logowania (zwykle hasła) i ograniczanie zasobów (często katalogów i plików), które użytkownik może uzyskać dostęp. Jednak takie podejście nie uda się rozwiązać pewne problemy: użytkownicy uzyskują kodu z wielu źródeł, niektóre z nich mogą być nieprawidłowe; Kod może zawierać usterki lub luk w zabezpieczeniach mogła zostać wykorzystana przez złośliwy kod; i kod czasami wykonuje czynności, które użytkownik nie może określić, że będzie wykonywał. W związku z tym może być uszkodzony systemów komputerowych i dane prywatne mogą przedostawać użytkowników ostrożność i zaufanego uruchomienie złośliwego lub wypełnione błąd oprogramowania. Większość mechanizmy zabezpieczeń systemu operacyjnego wymagają, że każdy fragment kodu musi być całkowicie zaufany niezbędne do uruchomienia, z wyjątkiem prawdopodobnie skryptów na stronie sieci Web. W związku z tym nadal istnieje potrzeba mechanizm powszechnie stosowane zabezpieczeń, który umożliwia kodu pochodzącego z jednego komputera do wykonania z ochrony w innym systemie, nawet gdy nie ma relacji zaufania między systemów.  
  
 .NET Framework zapewnia mechanizm zabezpieczeń o nazwie zabezpieczenia dostępu kodu w celu ochrony komputerów przed złośliwego kodu przenośnych, aby umożliwić kodu z nieznanego źródła, aby uruchomić z ochrony i ułatwia zapobieganie zaufanego kodu z celowo lub przypadkowo naruszenie zabezpieczeń. Zabezpieczenia dostępu kodu umożliwia kod, aby być uważany za zaufany w różnym stopniu, w zależności od których pochodzą kod i na innych aspektów tożsamości kodu. Zabezpieczenia dostępu kodu wymusza także różne poziomy zaufania kodu, co minimalizuje ilość kodu, który musi być w pełni zaufany, aby można było uruchomić. Przy użyciu zabezpieczenia dostępu kodu można zmniejszyć prawdopodobieństwo, że kod jest używane przez złośliwe lub wypełnione błąd kodu. Twoja odpowiedzialność go może zmniejszyć, ponieważ można określić zestaw kod powinien mieć możliwość wykonania operacji. Zabezpieczenia dostępu kodu może również pomóc ograniczyć potencjalne szkody, który może wynikać z luk w zabezpieczeniach w kodzie.  
  
> [!NOTE]
>  Zabezpieczenia dostępu kodu w wprowadzono istotne zmiany [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Najbardziej znaczące zmiany został [przezroczystość zabezpieczeń](../../../docs/framework/misc/security-transparent-code.md), ale istnieją także inne ważne zmiany, które mają wpływ na zabezpieczenia dostępu kodu. Aby uzyskać informacje o tych zmianach, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Zabezpieczenia dostępu kodu dotyczy przede wszystkim kod biblioteki i częściowo zaufane aplikacje. Deweloperzy biblioteki należy chronić ich kodu przed nieautoryzowanym dostępem z częściowo zaufane aplikacje. Częściowo zaufane aplikacje to aplikacje, które są ładowane z zewnętrznych źródeł, takich jak Internet. Aplikacje, które są instalowane na pulpicie lub w lokalnym intranecie uruchamiania w trybie pełnego zaufania. Aplikacje pełnego zaufania nie jest narażony na zabezpieczenia dostępu kodu, chyba że są one oznaczone jako [przezroczystym poziomie bezpieczeństwa](../../../docs/framework/misc/security-transparent-code.md), ponieważ są one w pełni zaufany. Jest to tylko ograniczenia dla aplikacji pełnego zaufania, że aplikacje, które są oznaczone ikoną z <xref:System.Security.SecurityTransparentAttribute> atrybutu nie można wywołać kod, który jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybutu. Częściowo zaufane aplikacje musi zostać uruchomiony w piaskownicy (na przykład w programie Internet Explorer), dzięki czemu można zastosować zabezpieczenia dostępu kodu. Jeśli pobieranie aplikacji z Internetu i spróbuj uruchomić go z pulpitu, otrzyma <xref:System.NotSupportedException> z komunikatem: "podjęto próbę załadowania zestawu z lokalizacji sieciowej, które mogłyby spowodować zestawu w trybie piaskownicy w poprzednich wersjach programu .NET Framework. Tej wersji programu .NET Framework nie zasady CAS domyślnie włączone, więc to załadowanie może być niebezpieczne." Jeśli masz pewność, że aplikacja jest zaufany, możesz je włączyć do uruchomienia przy pełnym zaufaniu przy użyciu [ \<loadFromRemoteSources > elementu](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Aby uzyskać informacje o uruchamianiu aplikacji w bibliotece, zobacz [porady: uruchamianie częściowo zaufanego kodu w bibliotece](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Środowisko uruchomieniowe języka wspólnego odbiera zalet zabezpieczeń dostępu kodu, którego element docelowy wszystkie zarządzane kodu, nawet jeśli ten kod nie oznacza, że zabezpieczenia dostępu kodu jednego wywołania. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Najważniejsze funkcje zabezpieczeń dostępu kodu  
 Zabezpieczenia dostępu kodu pomaga ograniczyć dostępu kodu do chronionych zasobów i operacji. W programie .NET Framework zabezpieczenia dostępu kodu wykonuje następujące funkcje:  
  
-   Definiuje uprawnienia i zestawów uprawnień, które reprezentują prawa dostępu różnych zasobów systemowych.  
  
-   Umożliwia kodu na żądanie, że elementy wywołujące pod ma określone uprawnienia.  
  
-   Umożliwia kodu na żądanie, aby elementy wywołujące pod posiadał podpisu cyfrowego, dzięki czemu tylko wywołującym z organizacji lub witryny wywoływać kod chronionych.  
  
-   Wymusza ograniczenia dotyczące kodu w czasie wykonywania na podstawie porównania ilości uprawnienia nadanego co wywołujący na stosie wywołań w celu wywoływania musi mieć uprawnienia.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Przejście stosu wywołań  
 Aby ustalić, czy kod jest autoryzowany do uzyskania dostępu do zasobu lub wykonania operacji, system zabezpieczeń środowiska uruchomieniowego przeprowadzi stos wywołań, porównanie uprawnienia nadanego każdy obiekt wywołujący, aby uprawnienia są wymagane. Jeśli każdego obiektu wywołującego w stosie wywołań nie ma wymaganego uprawnienia, jest zgłaszany wyjątek zabezpieczeń, a w przypadku odmowy dostępu. Podczas przeszukiwana stosu zaprojektowano w celu zapobieżenia zapewnienia ataków, w którym niższym poziomie zaufania kod wywołuje kod wysoce zaufanych i używa go do wykonywania akcji nieautoryzowanego. Potrzebują uprawnień wszystkim zainteresowanym w czasie wykonywania wpływa na wydajność, ale jest niezbędne w celu ochrony kodu z zapewnienia ataków przez kod niższym poziomie zaufania. Aby zoptymalizować wydajność, może mieć kod wykonania mniejszej liczby przeszukiwań stosu; jednak należy upewnić się, że nie ujawniaj osłabienia zabezpieczeń zawsze, gdy to zrobić.  
  
 Na poniższej ilustracji przedstawiono przeszukiwania stosu, który gdy metody w zestawie A4 wymaga, że jego obiektów wywołujących uprawnienie P.  
  
 ![Zabezpieczenia dostępu kodu](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Przeszukiwanie stosów zabezpieczeń  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md)|W tym artykule opisano zabezpieczenia dostępu kodu i jego najbardziej typowych zastosowań.|  
|[Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|W tym artykule opisano model przezroczystość zabezpieczeń w programie [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].|  
|[Używanie bibliotek pochodzących z częściowo zaufanego kodu](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|Opisuje sposób włączania biblioteki do użycia z kodem niezarządzanym i sposobu użycia bibliotek pochodzących z kodem niezarządzanym.|  
|[Główne pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md)|Zawiera omówienie wiele kluczowe terminy i pojęcia używane w systemie zabezpieczeń .NET Framework.|  
|[Zabezpieczenia oparte na rolach](../../../docs/standard/security/role-based-security.md)|Opisuje sposób zastosować zabezpieczenia oparte na rolach.|  
|[Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)|Opisuje sposób włączenia kryptografii do aplikacji.|
