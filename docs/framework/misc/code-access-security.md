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
ms.openlocfilehash: f7f089a4482173fd9697738c1643c33c05da4212
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910958"
---
# <a name="code-access-security"></a>Zabezpieczenia dostępu kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Współczesne systemy komputerowe o wysokiej dostępności są często uwidaczniane dla kodu pochodzącego z różnych, prawdopodobnie nieznanych źródeł. Kod można dołączyć do poczty e-mail, zawartej w dokumentach lub pobranej przez Internet. Niestety wielu użytkowników komputerów ręki skutki złośliwego kodu mobilnego, w tym wirusów i robaków, które mogą uszkodzić lub niszczyć dane, a także zaoszczędzić czas i pieniądze.  
  
 Większość typowych mechanizmów zabezpieczeń daje prawo użytkownikom na podstawie poświadczeń logowania (zwykle hasła) i ogranicza zasobów (często katalogów i plików), do których użytkownik może uzyskać dostęp. Niemniej jednak rozwiązanie nie rozwiąże się z kilkoma problemami: użytkownicy uzyskują kod z wielu źródeł, a niektóre z nich mogą być zawodne. kod może zawierać usterki lub luki w zabezpieczeniach, które umożliwiają wykorzystanie złośliwego kodu; a kod czasami robi, że użytkownik nie wie. W związku z tym systemy komputerowe mogą być uszkodzone, a dane prywatne mogą być przeciekowe, gdy ostrożność i godna zaufania użytkownicy uruchamiają złośliwe lub wypełnione przez nie oprogramowanie. Większość mechanizmów zabezpieczeń systemu operacyjnego wymaga, aby każdy fragment kodu musiał być całkowicie zaufany, aby można było go uruchomić, z wyjątkiem skryptów na stronie sieci Web. W związku z tym nadal konieczne jest stosowanie powszechnie stosowanego mechanizmu zabezpieczeń, który umożliwia wykonywanie kodu pochodzącego z jednego systemu komputerowego z ochroną w innym systemie nawet wtedy, gdy nie istnieje relacja zaufania między systemami.  
  
 .NET Framework zapewnia mechanizm zabezpieczeń o nazwie zabezpieczenia dostępu kodu, który pomaga chronić systemy komputerowe przed złośliwym kodem mobilnym, aby umożliwić uruchamianie kodu z nieznanych źródeł przy użyciu ochrony, a także zapobiegać celowemu lub przypadkowemu przypadkowi wystąpienia zaufania. naruszenie zabezpieczeń. Zabezpieczenia dostępu kodu umożliwiają ufanie kodowi różnym stopom w zależności od tego, skąd pochodzi kod, oraz od innych aspektów tożsamości kodu. Zabezpieczenia dostępu kodu wymuszają również różne poziomy zaufania w kodzie, co minimalizuje ilość kodu, który musi być w pełni zaufany, aby można było go uruchomić. Użycie zabezpieczeń dostępu kodu może zmniejszyć prawdopodobieństwo, że kod będzie nieużywany przez złośliwy lub niewypełniony kod. Może to zmniejszyć odpowiedzialność, ponieważ można określić zestaw operacji, które kod powinien wykonać. Zabezpieczenia dostępu kodu mogą również zminimalizować szkody, które mogą wynikać z luk w zabezpieczeniach w kodzie.  
  
> [!NOTE]
> Wprowadzono istotne zmiany w zabezpieczeniach dostępu kodu w .NET Framework 4. Najbardziej istotną zmianą jest [przejrzystość zabezpieczeń](../../../docs/framework/misc/security-transparent-code.md), ale istnieją również inne istotne zmiany, które wpływają na zabezpieczenia dostępu kodu. Aby uzyskać informacje o tych zmianach, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Zabezpieczenia dostępu kodu mają głównie wpływ na kod biblioteki i częściowo zaufane aplikacje. Deweloperzy bibliotek muszą chronić swój kod przed nieautoryzowanym dostępem z częściowo zaufanych aplikacji. Częściowo zaufane aplikacje są aplikacjami, które są ładowane ze źródeł zewnętrznych, takich jak Internet. Aplikacje zainstalowane na pulpicie lub w lokalnym intranecie działają w trybie pełnego zaufania. Zabezpieczenia dostępu kodu nie wpływają na aplikacje mające pełne zaufanie, chyba że są oznaczone jako przezroczyste dla [zabezpieczeń](../../../docs/framework/misc/security-transparent-code.md), ponieważ są w pełni zaufane. Jedynym ograniczeniem dla aplikacji w pełnym zaufaniu jest to, że aplikacje oznaczone <xref:System.Security.SecurityTransparentAttribute> atrybutem nie mogą wywołać kodu, który jest oznaczony <xref:System.Security.SecurityCriticalAttribute> za pomocą atrybutu. Częściowo zaufane aplikacje muszą być uruchamiane w piaskownicy (na przykład w programie Internet Explorer), aby można było zastosować zabezpieczenia dostępu kodu. Jeśli pobierzesz aplikację z Internetu i spróbujesz uruchomić ją z poziomu pulpitu, <xref:System.NotSupportedException> otrzymasz komunikat o błędzie: "Podjęto próbę załadowania zestawu z lokalizacji sieciowej, która spowodowała przełączenie zestawu do piaskownicy w poprzednich wersjach .NET Framework. Ta wersja .NET Framework nie domyślnie włącza zasad CAS, więc to obciążenie może być niebezpieczne. Jeśli masz pewność, że aplikacja może być zaufana, możesz ją uruchomić jako pełne zaufanie, używając [ \<elementu loadFromRemoteSources >](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Aby uzyskać informacje na temat uruchamiania aplikacji w piaskownicy, [zobacz How to: Uruchom częściowo zaufany kod w piaskownicy](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Cały kod zarządzany, który jest przeznaczony dla środowiska uruchomieniowego języka wspólnego, otrzymuje zalety zabezpieczenia dostępu kodu, nawet jeśli ten kod nie nawiąże wywołania zabezpieczeń pojedynczego kodu. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Najważniejsze funkcje zabezpieczeń dostępu kodu  
 Zabezpieczenia dostępu kodu pomagają ograniczyć dostęp tego kodu do chronionych zasobów i operacji. W .NET Framework zabezpieczenia dostępu kodu są wykonywane w następujących funkcjach:  
  
- Definiuje uprawnienia i zestawy uprawnień, które reprezentują prawo dostępu do różnych zasobów systemu.  
  
- Włącza kod do żądania, że jego obiekty wywołujące mają określone uprawnienia.  
  
- Umożliwia wykonywanie kodu na potrzeby żądania, że jego obiekty wywołujące mają podpis cyfrowy, co pozwala tylko wywołującym z danej organizacji lub lokacji wywoływanie chronionego kodu.  
  
- Wymusza ograniczenia dotyczące kodu w czasie wykonywania, porównując przyznane uprawnienia każdego obiektu wywołującego na stosie wywołań z uprawnieniami, które są wymagane przez wywoływania.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Instruktaż stosu wywołań  
 Aby ustalić, czy kod jest autoryzowany do uzyskania dostępu do zasobu lub wykonywania operacji, system zabezpieczeń środowiska uruchomieniowego sprawdza stos wywołań, porównując przyznane uprawnienia każdego wywołującego z przyznanym uprawnieniem. Jeśli jakikolwiek obiekt wywołujący w stosie wywołań nie ma wymaganego uprawnienia, zgłaszany jest wyjątek zabezpieczeń i nastąpiła odmowa dostępu. Funkcja przeszukiwania stosu pomaga zapobiegać atakom luring, w którym kod mniej zaufany wywołuje wysoce zaufany kod i używa go do wykonywania nieautoryzowanych akcji. Wysokie uprawnienia wszystkich obiektów wywołujących w czasie wykonywania mają wpływ na wydajność, ale ważne jest, aby chronić kod przed atakami luring przez kod mniej zaufany. Aby zoptymalizować wydajność, kod może być krótszy niż przeszukiwanie stosu. należy jednak pamiętać, że nie ujawniamy luki w zabezpieczeniach w dowolnym momencie.  
  
 Na poniższej ilustracji przedstawiono przeszukiwanie stosu, które powstaje, gdy metoda w zestawie A4 wymaga, aby jej wywołania miały uprawnienie P.  
  
 ![Zabezpieczenia dostępu kodu](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Omówienie stosu zabezpieczeń  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Podstawowe informacje o zabezpieczeniach dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md)|Opisuje zabezpieczenia dostępu kodu i jego najczęstsze zastosowania.|  
|[Kod przezroczysty pod względem zabezpieczeń, poziom 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|Opisuje model przezroczystości zabezpieczeń w .NET Framework 4.|  
|[Korzystanie z bibliotek z częściowo zaufanego kodu](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|Opisuje sposób włączania bibliotek do użycia z kodem niezarządzanym oraz jak używać bibliotek z kodu niezarządzanego.|  
|[Główne pojęcia dotyczące zabezpieczeń](../../standard/security/key-security-concepts.md)|Zawiera przegląd wielu najważniejszych pojęć i koncepcji używanych w systemie zabezpieczeń .NET Framework.|  
|[Zabezpieczenia oparte na rolach](../../standard/security/role-based-security.md)|Opisuje sposób włączania zabezpieczeń na podstawie ról.|  
|[Usługi kryptograficzne](../../standard/security/cryptographic-services.md)|Opisuje sposób włączania kryptografii do aplikacji.|
