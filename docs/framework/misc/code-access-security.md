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
ms.openlocfilehash: a7dce1efedfb652096e6b583eca08e5b80d282a5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645780"
---
# <a name="code-access-security"></a>Zabezpieczenia dostępu kodu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Dzisiejsze wysoce podłączone systemy komputerowe są często narażone na działanie kodu pochodzącego z różnych, prawdopodobnie nieznanych źródeł. Kod można dołączyć do wiadomości e-mail, zawierać w dokumentach lub pobrać przez Internet. Niestety, wielu użytkowników komputerów doświadczyło z pierwszej ręki skutków złośliwego kodu mobilnego, w tym wirusów i robaków, które mogą uszkodzić lub zniszczyć dane i kosztować czas i pieniądze.  
  
 Większość typowych mechanizmów zabezpieczeń daje użytkownikom prawa na podstawie poświadczeń logowania (zwykle hasło) i ograniczyć zasoby (często katalogi i pliki), do których użytkownik ma dostęp. Jednak to podejście nie rozwiązuje kilku problemów: użytkownicy uzyskują kod z wielu źródeł, z których niektóre mogą być zawodne; kod może zawierać błędy lub luki, które umożliwiają jego wykorzystanie przez złośliwy kod; i kod czasami robi rzeczy, które użytkownik nie wie, że zrobi. W rezultacie systemy komputerowe mogą ulec uszkodzeniu, a prywatne dane mogą zostać ujawnione, gdy ostrożni i zaufani użytkownicy uruchamiają złośliwe lub wypełnione błędami oprogramowanie. Większość mechanizmów zabezpieczeń systemu operacyjnego wymaga, aby każdy fragment kodu był całkowicie zaufany, aby można było go uruchomić, z wyjątkiem skryptów na stronie sieci Web. W związku z tym nadal istnieje potrzeba szeroko stosowanego mechanizmu zabezpieczeń, który umożliwia wykonanie kodu pochodzącego z jednego systemu komputerowego z ochroną w innym systemie, nawet jeśli nie ma relacji zaufania między systemami.  
  
 Program .NET Framework udostępnia mechanizm zabezpieczeń o nazwie zabezpieczenia dostępu do kodu, aby chronić systemy komputerowe przed złośliwym kodem mobilnym, aby umożliwić uruchamianie kodu z nieznanego pochodzenia z ochroną i zapobiegać celowemu lub przypadkowemu naruszaniu zabezpieczeń zaufanego kodu. Zabezpieczenia dostępu do kodu umożliwia kod jest zaufany w różnym stopniu w zależności od tego, skąd pochodzi kod i na inne aspekty tożsamości kodu. Zabezpieczenia dostępu do kodu wymusza również różne poziomy zaufania do kodu, co minimalizuje ilość kodu, który musi być w pełni zaufany, aby można było uruchomić. Za pomocą zabezpieczeń dostępu do kodu można zmniejszyć prawdopodobieństwo, że kod będzie niewłaściwie przez złośliwy lub wypełniony błędami kod. Może zmniejszyć swoje zobowiązanie, ponieważ można określić zestaw operacji, które kod powinien być dozwolony do wykonania. Zabezpieczenia dostępu do kodu mogą również pomóc zminimalizować szkody, które mogą wynikać z luk w zabezpieczeniach kodu.  
  
> [!NOTE]
> Wprowadzono istotne zmiany w zabezpieczeniach dostępu do kodu w programie .NET Framework 4. Najbardziej zauważalną zmianą była [przejrzystość zabezpieczeń,](security-transparent-code.md)ale istnieją również inne istotne zmiany, które wpływają na bezpieczeństwo dostępu do kodu. Aby uzyskać informacje o tych zmianach, zobacz [Zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Zabezpieczenia dostępu do kodu dotyczą przede wszystkim kodu biblioteki i częściowo zaufanych aplikacji. Deweloperzy biblioteki muszą chronić swój kod przed nieautoryzowanym dostępem z częściowo zaufanych aplikacji. Częściowo zaufane aplikacje to aplikacje ładowane ze źródeł zewnętrznych, takich jak Internet. Aplikacje zainstalowane na pulpicie lub w lokalnym intranecie działają w pełnym zaufaniu. Zabezpieczenia dostępu do kodu nie mają wpływu na aplikacje pełne zaufania, chyba że są oznaczone jako przezroczyste dla [zabezpieczeń,](security-transparent-code.md)ponieważ są w pełni zaufane. Jedynym ograniczeniem dla aplikacji pełnego zaufania jest to, że aplikacje oznaczone atrybutem <xref:System.Security.SecurityTransparentAttribute> nie można wywołać kod, który jest oznaczony atrybutem. <xref:System.Security.SecurityCriticalAttribute> Częściowo zaufane aplikacje muszą być uruchamiane w piaskownicy (na przykład w programie Internet Explorer), aby można było zastosować zabezpieczenia dostępu do kodu. Jeśli pobierzesz aplikację z Internetu i spróbujesz uruchomić ją <xref:System.NotSupportedException> z pulpitu, otrzymasz komunikat: "Podjęto próbę załadowania zestawu z lokalizacji sieciowej, co spowodowałoby, że zestaw został wysysany w trybie piaskownicy w poprzednich wersjach programu .NET Framework. Ta wersja programu .NET Framework domyślnie nie włącza zasad CAS, więc to obciążenie może być niebezpieczne." Jeśli masz pewność, że aplikacja może być zaufana, można włączyć ją do uruchomienia jako pełne zaufanie przy użyciu [ \<loadFromRemoteSources> element](../configure-apps/file-schema/runtime/loadfromremotesources-element.md). Aby uzyskać informacje na temat uruchamiania aplikacji w piaskownicy, zobacz [Jak: Uruchamianie częściowo zaufanego kodu w piaskownicy](how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Cały kod zarządzany, który jest przeznaczony dla środowiska wykonawczego języka wspólnego otrzymuje korzyści z zabezpieczeń dostępu do kodu, nawet jeśli ten kod nie powoduje wywołania zabezpieczeń dostępu do pojedynczego kodu. Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](code-access-security-basics.md).  
  
<a name="key_functions"></a>
## <a name="key-functions-of-code-access-security"></a>Kluczowe funkcje zabezpieczeń dostępu do kodu  
 Zabezpieczenia dostępu do kodu pomaga ograniczyć dostęp, który kod ma do chronionych zasobów i operacji. W programie .NET Framework zabezpieczenia dostępu do kodu wykonują następujące funkcje:  
  
- Definiuje uprawnienia i zestawy uprawnień, które reprezentują prawo dostępu do różnych zasobów systemowych.  
  
- Umożliwia kod do żądania, że jego wywołujących mają określone uprawnienia.  
  
- Umożliwia kod do żądania, że jego wywołujących posiadają podpis cyfrowy, umożliwiając w ten sposób tylko wywołujących z określonej organizacji lub witryny do wywołania chronionego kodu.  
  
- Wymusza ograniczenia dotyczące kodu w czasie wykonywania, porównując przyznane uprawnienia każdego wywołującego na stosie wywołań do uprawnień, które muszą mieć wywołujący.  
  
<a name="walking_the_call_stack"></a>
## <a name="walking-the-call-stack"></a>Chodzenie po stosie połączeń  
 Aby ustalić, czy kod jest autoryzowany do dostępu do zasobu lub wykonywania operacji, system zabezpieczeń środowiska wykonawczego przechadza stos wywołań, porównując przyznane uprawnienia każdego obiektu wywołującego z wymaganym uprawnieniem. Jeśli dowolna wywołująca w stosie wywołań nie ma wymaganych uprawnień, wyjątek zabezpieczeń jest zgłaszany i odmawia się dostępu. Spacer stosu ma na celu zapobieganie atakom zwabiania, w którym mniej zaufany kod wywołuje wysoce zaufany kod i używa go do wykonywania nieautoryzowanych akcji. Żądanie uprawnień wszystkich wywołań w czasie wykonywania wpływa na wydajność, ale ważne jest, aby chronić kod przed atakami przez mniej zaufany kod. Aby zoptymalizować wydajność, można mieć kodu wykonać mniej spacerów stosu; jednak musisz mieć pewność, że nie narażasz się na słabość zabezpieczeń, gdy to zrobisz.  
  
 Na poniższej ilustracji przedstawiono spacer stosu, który powoduje, gdy metoda w zestawie A4 wymaga, aby jego rozmówcy mają uprawnienia P.  
  
 ![Zabezpieczenia dostępu do kodu](media/slide-10a.gif "slide_10a")  
Spacer ze stosem zabezpieczeń  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Podstawy zabezpieczeń dostępu kodu](code-access-security-basics.md)|W tym artykule opisano zabezpieczenia dostępu do kodu i jego najbardziej typowe zastosowania.|  
|[Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](security-transparent-code-level-2.md)|W tym artykule opisano model przezroczystości zabezpieczeń w .NET Framework 4.|  
|[Używanie bibliotek pochodzących z częściowo zaufanego kodu](using-libraries-from-partially-trusted-code.md)|W tym artykule opisano, jak włączyć biblioteki do użytku z kodem niezarządzanym i jak używać bibliotek z kodu niezarządzanego.|  
|[Główne pojęcia dotyczące zabezpieczeń](../../standard/security/key-security-concepts.md)|Zawiera omówienie wielu kluczowych terminów i pojęć używanych w systemie zabezpieczeń .NET Framework.|  
|[Zabezpieczenia oparte na rolach](../../standard/security/role-based-security.md)|W tym artykule opisano sposób włączania zabezpieczeń na podstawie ról.|  
|[Usługi kryptograficzne](../../standard/security/cryptographic-services.md)|W tym artykule opisano sposób włączania kryptografii do aplikacji.|
