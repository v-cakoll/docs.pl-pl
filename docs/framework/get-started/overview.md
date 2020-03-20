---
title: Przegląd programu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
ms.openlocfilehash: de9cbdab5d5786b9d59d23ba675fa3f78f807716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181590"
---
# <a name="overview-of-net-framework"></a>Omówienie programu .NET Framework

Program .NET Framework to technologia, która obsługuje tworzenie i uruchamianie aplikacji i usług sieci Web systemu Windows. Program .NET Framework został zaprojektowany w celu osiągnięcia następujących celów:

- Aby zapewnić spójne środowisko programowania obiektowego obiektowego, czy kod obiektu jest przechowywany i wykonywany lokalnie, wykonywane lokalnie, ale dystrybuowane w sieci Web lub wykonywane zdalnie.

- Aby zapewnić środowisko wykonywania kodu, które minimalizuje konflikty wdrażania oprogramowania i przechowywania wersji.

- Aby zapewnić środowisko wykonywania kodu, które promuje bezpieczne wykonywanie kodu, w tym kod utworzony przez nieznaną lub częściowo zaufaną stronę trzecią.

- Aby zapewnić środowisko wykonywania kodu, które eliminuje problemy z wydajnością środowisk skryptowych lub interpretowanych.

- Aby środowisko dewelopera było spójne w przypadku aplikacji o różnych typach, takich jak aplikacje oparte na systemie Windows i aplikacje oparte na sieci Web.

- Aby utworzyć całą komunikację na standardach branżowych, aby upewnić się, że kod oparty na programie .NET Framework integruje się z dowolnym innym kodem.

> [!NOTE]
> Aby uzyskać ogólne wprowadzenie do programu .NET Framework zarówno dla użytkowników, jak i deweloperów, zobacz [Wprowadzenie](index.md).

Program .NET Framework składa się ze środowiska wykonawczego języka wspólnego (CLR) i biblioteki klas programu .NET Framework. Środowisko wykonawcze języka wspólnego jest podstawą programu .NET Framework. Pomyśl o czasie wykonywania jako agent, który zarządza kodem w czasie wykonywania, zapewniając podstawowe usługi, takie jak zarządzanie pamięcią, zarządzanie wątkami i komunikacji zdalnej, a także wymuszanie ścisłego bezpieczeństwa typu i innych form dokładności kodu, które promują bezpieczeństwo i niezawodność. W rzeczywistości pojęcie zarządzania kodem jest podstawową zasadą środowiska wykonawczego. Kod, który jest przeznaczony dla środowiska wykonawczego jest znany jako kod zarządzany, podczas gdy kod, który nie jest przeznaczony dla środowiska wykonawczego jest znany jako kod niezarządzany. Biblioteka klas to kompleksowa, obiektowa kolekcja typów wielokrotnego użytku, których używasz do tworzenia aplikacji, od tradycyjnych aplikacji wiersza polecenia lub graficznego interfejsu użytkownika (GUI) po aplikacje oparte na najnowszych innowacjach dostarczanych przez ASP.NET, takich jak Web Formularze i usługi sieci Web XML.

Program .NET Framework może być obsługiwany przez składniki niezarządzane, które ładują środowisko uruchomieniowe języka wspólnego do swoich procesów i inicjują wykonywanie kodu zarządzanego, tworząc w ten sposób środowisko oprogramowania wykorzystujące zarówno funkcje zarządzane, jak i niezarządzane. Program .NET Framework nie tylko udostępnia kilka hostów środowiska uruchomieniowego, ale także obsługuje tworzenie hostów środowiska uruchomieniowego innych firm.

Na przykład ASP.NET hostuje środowisko wykonawcze, aby zapewnić skalowalne środowisko po stronie serwera dla kodu zarządzanego. ASP.NET działa bezpośrednio ze środowiska wykonawczego, aby włączyć ASP.NET aplikacji i usług sieci web XML, z których oba zostały omówione w dalszej części tego artykułu.

Program Internet Explorer jest przykładem niezarządzanej aplikacji, która obsługuje środowisko wykonawcze (w postaci rozszerzenia typu MIME). Używanie programu Internet Explorer do hosta środowiska wykonawczego umożliwia osadzanie składników zarządzanych lub formantów windows forms w dokumentach HTML. Hostowanie środowiska wykonawczego w ten sposób umożliwia zarządzany kod mobilny, ale ze znacznymi ulepszeniami, które oferuje tylko kod zarządzany, takimi jak półufane wykonanie i izolowany magazyn plików.

Na poniższej ilustracji przedstawiono relację środowiska wykonawczego języka wspólnego i biblioteki klas z aplikacjami i ogólnym systemem. Ilustracja pokazuje również, jak kod zarządzany działa w ramach większej architektury.

![Zrzut ekranu przedstawiający sposób działania kodu zarządzanego w ramach większej architektury.](./media/overview/language-runtime-class-library-relationship.gif)

W poniższych sekcjach opisano główne funkcje programu .NET Framework bardziej szczegółowo.

## <a name="features-of-the-common-language-runtime"></a>Funkcje wspólnego środowiska wykonawczego języka

Środowisko wykonawcze języka wspólnego zarządza pamięcią, wykonywaniem wątków, wykonywaniem kodu, weryfikacją bezpieczeństwa kodu, kompilacją i innymi usługami systemowymi. Te funkcje są nieodłączne dla kodu zarządzanego, który działa w czasie wykonywania języka wspólnego.

Jeśli chodzi o zabezpieczenia, zarządzane składniki są przyznawane w różnym stopniu zaufania, w zależności od wielu czynników, które obejmują ich pochodzenie (takie jak Internet, sieć przedsiębiorstwa lub komputer lokalny). Oznacza to, że składnik zarządzany może lub może nie być w stanie wykonać operacje dostępu do plików, operacji dostępu do rejestru lub innych poufnych funkcji, nawet jeśli jest używany w tej samej aktywnej aplikacji.

Środowisko wykonawcze wymusza również niezawodność kodu, implementując ścisłą infrastrukturę weryfikacji typu i kodu o nazwie system typu wspólnego (CTS). CTS zapewnia, że cały kod zarządzany jest samookrywanie. Różne kompilatory języka firmy Microsoft i innych firm generują kod zarządzany zgodny z systemem CTS. Oznacza to, że kod zarządzany może korzystać z innych typów zarządzanych i wystąpień, przy jednoczesnym ścisłym wymuszaniu wierności typu i bezpieczeństwa typu.

Ponadto zarządzane środowisko środowiska wykonawczego eliminuje wiele typowych problemów z oprogramowaniem. Na przykład środowisko wykonawcze automatycznie obsługuje układ obiektu i zarządza odwołaniami do obiektów, zwalniając je, gdy nie są już używane. To automatyczne zarządzanie pamięcią rozwiązuje dwa najczęstsze błędy aplikacji, przecieki pamięci i nieprawidłowe odwołania do pamięci.

Środowisko wykonawcze przyspiesza również produktywność deweloperów. Na przykład programiści piszą aplikacje w wybranym języku programowania, ale w pełni wykorzystują środowisko wykonawcze, bibliotekę klas i składniki napisane w innych językach przez innych deweloperów. Każdy dostawca kompilatora, który zdecyduje się na kierowanie środowiska wykonawczego może to zrobić. Kompilatory języka, które są przeznaczone dla programu .NET Framework udostępnić funkcje programu .NET Framework do istniejącego kodu napisanego w tym języku, znacznie ułatwiając proces migracji dla istniejących aplikacji.

Podczas gdy środowisko wykonawcze jest przeznaczone dla oprogramowania przyszłości, obsługuje również oprogramowanie dzisiaj i wczoraj. Współdziałanie między kodem zarządzanym i niezarządzanym umożliwia deweloperom dalsze używanie niezbędnych składników COM i bibliotek DLL.

Środowisko wykonawcze ma na celu zwiększenie wydajności. Chociaż środowisko uruchomieniowe języka wspólnego zapewnia wiele standardowych usług środowiska uruchomieniowego, kod zarządzany nigdy nie jest interpretowany. Funkcja o nazwie kompilacji just-in-time (JIT) umożliwia wszystkie zarządzane kodu do uruchomienia w języku macierzystym maszyny systemu, w którym jest wykonywany. Tymczasem menedżer pamięci usuwa możliwości pamięci pofragmentowanej i zwiększa lokalizacja pamięci odniesienia do dalszego zwiększenia wydajności.

Na koniec środowisko wykonawcze może być hostowane przez aplikacje po stronie serwera o wysokiej wydajności, takie jak Microsoft SQL Server i internet information services (IIS). Ta infrastruktura umożliwia używanie kodu zarządzanego do pisania logiki biznesowej, a jednocześnie cieszyć się najwyższą wydajnością najlepszych w branży serwerów korporacyjnych obsługujących hosting środowiska uruchomieniowego.

## <a name="net-framework-class-library"></a>Biblioteka klas programu .NET Framework

Biblioteka klas .NET Framework jest zbiorem typów wielokrotnegoużytnia, które ściśle integrują się ze wspólnym środowiskom uruchomieniowym języka. Biblioteka klas jest zorientowana obiektowo, zapewniając typy, z których własny kod zarządzany wywodzi funkcjonalność. To nie tylko sprawia, że typy .NET Framework łatwe w użyciu, ale także skraca czas związany z uczenia się nowych funkcji programu .NET Framework. Ponadto składniki innych firm bezproblemowo integrują się z klasami w ramach .NET Framework.

Na przykład klasy zbierania .NET Framework implementują zestaw interfejsów do tworzenia własnych klas kolekcji. Klasy kolekcji płynnie łączą się z klasami w .NET Framework.

Zgodnie z oczekiwaniami z biblioteki klas obiektowych typy .NET Framework umożliwiają wykonywanie szeregu typowych zadań programowania, w tym zadań, takich jak zarządzanie ciągami, zbieranie danych, łączność z bazą danych i dostęp do plików. Oprócz tych typowych zadań biblioteka klas zawiera typy, które obsługują różne scenariusze rozwoju specjalistycznego. Użyj programu .NET Framework do tworzenia następujących typów aplikacji i usług:

- Aplikacje konsoli. Zobacz [Tworzenie aplikacji konsoli](../../standard/building-console-apps.md).

- Aplikacje graficzne systemu Windows (Formularze systemu Windows). Zobacz [Formularze systemu Windows](../winforms/index.md).

- aplikacje Programu Windows Presentation Foundation (WPF). Zobacz [Fundacja prezentacji systemu Windows](../wpf/index.md).

- ASP.NET aplikacje. Zobacz [Aplikacje sieci Web z ASP.NET](../develop-web-apps-with-aspnet.md).

- Usługi systemu Windows. Zobacz [Wprowadzenie do aplikacji usługi systemu Windows](../windows-services/introduction-to-windows-service-applications.md).

- Aplikacje zorientowane na usługi przy użyciu programu Windows Communication Foundation (WCF). Zobacz [Aplikacje zorientowane na usługi z WCF](../wcf/index.md).

- Aplikacje z obsługą przepływu pracy przy użyciu programu Windows Workflow Foundation (WF). Zobacz [Windows Workflow Foundation](../windows-workflow-foundation/index.md).

Klasy Formularze systemu Windows to kompleksowy zestaw typów wielokrotnego pożytezowego, które znacznie upraszczają tworzenie interfejsu użytkownika interfejsu użytkownika systemu Windows. Jeśli piszesz ASP.NET aplikacji formularz sieci Web, możesz użyć klas Formularze sieci Web.

## <a name="see-also"></a>Zobacz też

- [Wymagania systemowe](system-requirements.md)
- [Instrukcja instalacji](../install/index.md)
- [Podręcznik programowania](../development-guide.md)
- [narzędzia](../tools/index.md)
- [Przykłady i samouczki platformy .NET](../../samples-and-tutorials/index.md)
- [Przeglądarka interfejsu API platformy .NET](../../../api/index.md)
