---
title: Zabezpieczenia dostępu kodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c8508b4ba7d6ac6e25fdcc70fb8162b8908e8fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592865"
---
# <a name="code-access-security"></a>Zabezpieczenia dostępu kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Systemów komputerowych o wysokim stopniu połączenia współczesnych często są widoczne dla kodu pochodzących z różnych, prawdopodobnie nieznanych źródeł. Kod można dołączyć do wiadomości e-mail, zawartych w dokumentach lub pobrane z Internetu. Niestety wielu użytkowników komputera wystąpić całodniowej skutki złośliwego kodu mobilnych, w tym wirusów i robaków, które uszkodzenia lub zniszczenia danych i koszt czasu i pieniędzy.  
  
 Najbardziej popularne mechanizmy zabezpieczeń udzielić uprawnień do użytkowników na podstawie ich poświadczeń logowania (zwykle hasła) i ograniczenie zasobów (często katalogów i plików), które użytkownik może uzyskać dostęp do. Jednak to podejście nie powiedzie się kilka problemów: użytkownicy uzyskują kod z wielu źródeł, z których część może być zawodne; Kod może zawierać błędy lub usterki, umożliwiających realizację zostać wykorzystana przez złośliwy kod; i kod realizuje czasami rzeczy, które użytkownik nie będzie wiadomo, że będzie on wykonywać. W rezultacie systemy komputerowe mogą być uszkodzone i dane prywatne mogą przedostawać się podczas uruchamiania złośliwego lub wypełnione błąd oprogramowania przez użytkowników zachować ostrożność i godne zaufania. Większość mechanizmów zabezpieczeń systemu operacyjnego wymagają, że każdy fragment kodu musi być całkowicie zaufanych aby można było uruchomić, z wyjątkiem prawdopodobnie skrypty na stronie sieci Web. W związku z tym nadal istnieje potrzeba mechanizm powszechnie stosowanych zabezpieczeń, który umożliwia kodu pochodzących z jednego komputera do wykonania przy użyciu ochrony w innym systemie, nawet wtedy, gdy istnieje relacja zaufania między systemami.  
  
 Program .NET Framework dostarcza mechanizm zabezpieczeń o nazwie zabezpieczenia dostępu kodu w celu ochrony systemów komputerowych przed złośliwego kodu mobilnych, aby umożliwić kodu z nieznanego źródła do uruchamiania przy użyciu ochrony, a także pomaga zapobiegać zaufanego kodu z celowo lub przypadkowo zagrożenia dla bezpieczeństwa. Zabezpieczenia dostępu kodu umożliwia kodu być uważany za zaufany w różnym stopniu, w zależności od tego, gdzie kod pochodzi, a także na innych aspektów tożsamości kodu. Zabezpieczenia dostępu kodu wymusza także różne poziomy zaufania w kodzie, co zmniejsza ilość kodu, który musi być w pełni zaufany, aby można było uruchomić. Przy użyciu zabezpieczeń dostępu kodu może zmniejszyć prawdopodobieństwo, że Twój kod będzie używane przez złośliwe lub wypełnione błąd kodu. Można jej zmniejszyć Twoja odpowiedzialność, ponieważ możesz określić zestaw operacji, które Twój kod powinien być dozwolony do wykonania. Zabezpieczenia dostępu kodu może również pomóc ograniczyć potencjalne szkody, która może spowodować luki w zabezpieczeniach w kodzie.  
  
> [!NOTE]
>  Wprowadzono znaczące zmiany zabezpieczeń dostępu kodu w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Najbardziej znacząca zmiana została [przezroczystości zabezpieczeń](../../../docs/framework/misc/security-transparent-code.md), ale istnieją także inne ważne zmiany, które mają wpływ na zabezpieczenia dostępu kodu. Aby uzyskać informacje o tych zmianach, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Zabezpieczenia dostępu kodu dotyczy przede wszystkim kod biblioteki i częściowo zaufanych aplikacji. Deweloperzy biblioteki należy chronić swój kod przed nieautoryzowanym dostępem z częściowo zaufanych aplikacji. Częściowo zaufane aplikacje to aplikacje, które zostały załadowane z zewnętrznych źródeł, takich jak Internet. Aplikacje, które są instalowane na pulpicie lub w lokalnym intranecie uruchamiania w trybie pełnego zaufania. Aplikacje pełnego zaufania nie dotyczy zabezpieczenia dostępu kodu, chyba że są one oznaczone jako [zabezpieczenia przejrzysty](../../../docs/framework/misc/security-transparent-code.md), ponieważ są w pełni zaufane. Jedynym ograniczeniem dla pełnego zaufania aplikacji jest fakt, że aplikacje, które są oznaczone <xref:System.Security.SecurityTransparentAttribute> atrybutu nie można wywołać kod, który jest oznaczony przy użyciu <xref:System.Security.SecurityCriticalAttribute> atrybutu. Częściowo zaufane aplikacje należy uruchomić w piaskownicy (na przykład w programie Internet Explorer), dzięki czemu można stosować zabezpieczenia dostępu kodu. Jeśli pobieranie aplikacji z Internetu i spróbuj uruchomić go z pulpitu, zostanie wyświetlony <xref:System.NotSupportedException> z komunikatem: "Podjęto próbę załadowania zestawu z lokalizacji sieciowej, która spowodowałaby zestawie, który ma być w trybie piaskownicy w poprzednich wersjach programu .NET Framework. Ta wersja programu .NET Framework nie włącza zasady CAS domyślnie, więc tego obciążenia może być niebezpieczne." Jeśli masz pewność, że aplikacja może być zaufane, można włączyć go do uruchamiania jako pełnego zaufania za pomocą [ \<loadfromremotesources — > element](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Aby dowiedzieć się, jak uruchomienie aplikacji w piaskownicy, zobacz [jak: Uruchamianie częściowo zaufanego kodu w piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Wszystkie zarządzane kodu przeznaczonego środowiska uruchomieniowego języka wspólnego odbiera korzyści z zabezpieczeń dostępu kodu, nawet wtedy, gdy ten kod nie oznacza, że zabezpieczenia dostępu kodu jednego, wywołania. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Kluczowe funkcje zabezpieczeń dostępu kodu  
 Zabezpieczenia dostępu kodu pomaga ograniczać dostęp do tego kodu do chronionych zasobów i operacji. W .NET Framework zabezpieczenia dostępu kodu wykonuje następujące funkcje:  
  
- Definiuje uprawnienia i zestawów uprawnień, które reprezentuje prawo dostępu do różnych zasobów systemowych.  
  
- Umożliwia kodu zapotrzebowania, że elementy go wywołujące pod ma określone uprawnienia.  
  
- Umożliwia kodu zapotrzebowania, że elementy go wywołujące pod posiadają podpis cyfrowy, dzięki czemu tylko obiekty wywołujące z konkretnej organizacji lub witryny do wywołania chronionego kodu.  
  
- Wymusza ograniczenia dotyczące kodu w czasie wykonywania, porównując udzielone uprawnienia co obiekt wywołujący na stosie wywołań do uprawnień, które musi zawierać obiekty wywołujące.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Zalet stosu wywołań  
 Aby ustalić, czy kod jest autoryzowany do uzyskania dostępu do zasobu lub wykonania operacji, system zabezpieczeń w środowisku uruchomieniowym przedstawia stos wywołań, porównywanie udzielone uprawnienia każdy obiekt wywołujący, aby uprawnienia są wymagane. Jeśli dowolny obiekt wywołujący na stosie wywołań nie ma wymaganego uprawnienia, jest zgłaszany wyjątek zabezpieczeń i następuje odmowa dostępu. Przeszukiwania stosu zaprojektowano w celu zapobieżenia zapewnienia ataków, w którym niższym poziomie zaufania kod wywołuje wysoce zaufanym kodem i używa go do wykonywania akcji nieautoryzowanego. Wymagających uprawnienia wszystkich obiektów wywołujących w czasie wykonywania wpływa na wydajność, ale jest niezbędne w celu ochrony kodu zapewnienia ataki przez kod niższym poziomie zaufania. Aby zoptymalizować wydajność, może mieć kod wykonania mniejszej liczby przeszukiwań stosu; jednak należy się upewnić, że nie ujawniaj do osłabienia zabezpieczeń zawsze wtedy, gdy to zrobisz.  
  
 Na poniższej ilustracji przedstawiono przeszukiwania stosu, która powstaje, gdy metody w zestawie A4 zapotrzebowania na to, że wywołujące uprawnienie P.  
  
 ![Zabezpieczenia dostępu kodu](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Przeszukiwania stosu zabezpieczeń  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md)|Opisuje zabezpieczenia dostępu kodu i jego najbardziej typowych zastosowań.|  
|[Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|Zawiera opis zabezpieczeń modelu przezroczystości w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].|  
|[Używanie bibliotek pochodzących z częściowo zaufanego kodu](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|W tym artykule opisano sposób włączania biblioteki do użycia z kodem niezarządzanym oraz jak wykorzystać biblioteki z niezarządzanego kodu.|  
|[Główne pojęcia dotyczące zabezpieczeń](../../../docs/standard/security/key-security-concepts.md)|Zawiera omówienie wiele kluczowe terminy i pojęcia używane w systemie zabezpieczeń .NET Framework.|  
|[Zabezpieczenia oparte na rolach](../../../docs/standard/security/role-based-security.md)|W tym artykule opisano, jak włączyć zabezpieczenia oparte na rolach.|  
|[Usługi kryptograficzne](../../../docs/standard/security/cryptographic-services.md)|Opisuje sposób włączenia kryptografii do aplikacji.|
