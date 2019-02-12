---
title: Przegląd programu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4aad615df6db5a29b9af21b585ea2b0dfbdedf4
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093687"
---
# <a name="overview-of-the-net-framework"></a>Przegląd programu .NET Framework

.NET Framework jest technologią, która obsługuje tworzenie i używanie kolejnej generacji aplikacji i usług sieci Web XML. .NET Framework jest zaprojektowany, aby wypełnić następujące cele:

- Zapewnianie spójnego zorientowane obiektowo środowiska programowania, czy kod obiektu jest przechowywany i wykonywany lokalnie, wykonywany lokalnie, ale rozproszony w Internecie, czy wykonywany zdalnie.

- Zapewnienie środowiska wykonania kodu, które minimalizuje konflikty wdrażaniem i przechowywaniem wersji oprogramowania.

- Zapewnienie środowiska wykonania kodu, które ułatwia bezpieczne wykonywanie kodu, w tym kodu utworzonego przez nieznaną lub na wpół zaufanych stronę trzecią.

- Aby zapewnić wykonywanie kodu środowiska, które eliminuje problemy z wydajnością inicjowanych przez skrypty lub interpretowane środowiska.

- Aby doświadczenia dewelopera spójne w różnych typach aplikacji, takich jak aplikacje oparte na Windows i aplikacji opartych na sieci Web.

- Tworzenie całej komunikacji na podstawie standardów przemysłowych w celu zapewnienia, że kod oparty na programie .NET Framework integruje się z innym kodem.

> [!NOTE]
> Aby uzyskać ogólne wprowadzenie do programu .NET Framework dla użytkowników i deweloperów — zobacz [wprowadzenie](../../../docs/framework/get-started/index.md).

.NET Framework składa się środowisko uruchomieniowe języka wspólnego (CLR) i biblioteki klas programu .NET Framework. Środowisko uruchomieniowe języka wspólnego jest podstawą środowiska .NET Framework. Środowisko wykonawcze można traktować jak agenta zarządzającego kodem w czasie wykonywania, dostarczającego usługi podstawowe, takie jak zarządzanie pamięcią, zarządzanie wątkami i obsługa zdalna, również wymuszając ścisłe zasady zabezpieczeń i inne formy dokładności kodu, które promują bezpieczeństwo i niezawodność. W rzeczywistości koncepcja zarządzania kodem jest podstawową zasadą środowiska wykonawczego. Kod, elementy docelowe środowisko uruchomieniowe jest znany jako kodu zarządzanego, gdy kod, który nie jest kierowana środowiska uruchomieniowego jest znany jako kod niezarządzany. Biblioteka klas jest kompleksowe, zorientowana obiektowo Kolekcja typów wielokrotnego użytku, które umożliwia tworzenie aplikacji od tradycyjnych użytkownika z wiersza polecenia lub graficznego interfejsu aplikacji (GUI) do aplikacji opartych na najnowszych innowacjach dostępnych w ASP.NET, takich jak sieci Web Formularze i usługi XML sieci Web.

.NET Framework może być obsługiwany przez składniki niezarządzane, których ładowanie środowiska uruchomieniowego języka wspólnego w swoje procesy i inicjują wykonywanie kodu zarządzanego, tworząc w ten sposób środowisko oprogramowania, które wykorzystuje funkcje zarządzanych i niezarządzanych. .NET Framework nie tylko udostępnia kilka hostów wykonawczych, ale również wspiera projektowanie hostów środowiska uruchomieniowego innych firm.

Na przykład platforma ASP.NET hostuje środowisko wykonawcze zapewniające skalowalne i po stronie serwera środowisko dla kodu zarządzanego. ASP.NET współpracuje bezpośrednio ze środowiska uruchomieniowego, aby umożliwić aplikacji ASP.NET i usługi XML sieci Web, które zostały omówione w dalszej części tego tematu.

Program Internet Explorer jest przykładem niezarządzanej aplikacji, która hostuje środowisko wykonawcze (w formie rozszerzeń typu MIME). Obsługa środowiska uruchomieniowego za pomocą programu Internet Explorer umożliwia osadzanie składników zarządzanych lub formantów formularzy Windows w dokumentach HTML. Hostowanie środowiska uruchomieniowego w ten sposób umożliwia zarządzanego kodu mobilnego, ale z znaczne ulepszenia oferuje tylko kod zarządzany, takie jak wykonanie półzaufane i izolowany magazyn plików.

Poniższa ilustracja pokazuje relację środowiska uruchomieniowego języka wspólnego i biblioteki klas, aplikacjach i całego systemu. Na ilustracji pokazano również działanie kodu zarządzanego działa w większej architekturze.

![Zarządzany kod w obrębie większej architekturze](../../../docs/framework/get-started/media/circle.gif "okrąg") .NET Framework w kontekście

Główne funkcje programu .NET Framework większej liczby szczegółów można znaleźć w poniższych sekcjach.

## <a name="features-of-the-common-language-runtime"></a>Funkcje środowiska uruchomieniowego języka wspólnego

Środowisko uruchomieniowe języka wspólnego zarządza, pamięci, wykonywaniem wątków, wykonywaniem kodu, weryfikacją bezpieczeństwa kodu, kompilacji i innych usług systemu. Funkcje te są nierozerwalnie związane z kodem zarządzanym, które jest uruchamiane na środowisko uruchomieniowe języka wspólnego.

Dotyczące zabezpieczeń składnikom zarządzanym są przyznawane różne stopnie zaufania w zależności od szeregu czynników, w tym ich pochodzenia (na przykład Internet, sieć przedsiębiorstwa lub komputer lokalny). Oznacza to, że zarządzany składnik może lub nie może być możliwe do wykonania operacji uzyskiwania dostępu do plików, operacje dostępu do rejestru lub innych ważnych funkcji, nawet jeśli jest on używany w tej samej aktywnej aplikacji.

Środowisko wykonawcze wymusza także niezawodność kodu poprzez implementację strict infrastruktury weryfikacji typu i kodu o nazwie system typu wspólnego (CTS). CTS zapewnia, że cały zarządzany kod jest samoopisujący. Różne firmy Microsoft i Kompilatory języka innych firm, generowanie kodu zarządzanego, który odpowiada CTS. Oznacza to, że kod zarządzany może zużywać inne zarządzane typy i wystąpienia, jednocześnie ściśle wymuszając wierność i bezpieczeństwo typów.

Ponadto zarządzane środowisko wykonawcze eliminuje wiele typowych problemów z oprogramowaniem. Na przykład środowisko wykonawcze automatycznie obsługuje układ obiektu i zarządza odwołaniami do obiektów, zwalniając je, gdy są one już używane. To automatyczne zarządzanie pamięcią usuwa dwa najbardziej typowych błędów aplikacji, przecieki pamięci i błędne odwołania do pamięci.

Środowisko wykonawcze przyspiesza również wydajność deweloperów. Na przykład programiści pisać aplikacje w ich z wybranego języka programowania, ale umożliwiają pełne wykorzystywanie zalet środowisko uruchomieniowe, biblioteki klas i składników napisanych w innych językach przez innych programistów. Każdy dostawca kompilatora, który chce przeznaczone dla środowiska uruchomieniowego można to zrobić. Kompilatory języka, które obsługują program .NET Framework udostępnia funkcje programu .NET Framework z istniejącym kodem w tym języku, znacznie ułatwianie proces migracji istniejących aplikacji.

Chociaż środowisko uruchomieniowe jest przeznaczone dla przyszłego oprogramowania, obsługuje również oprogramowanie działające dzisiaj i wczoraj. Współdziałanie między kodem zarządzanym i niezarządzanym umożliwia deweloperom kontynuować używanie niezbędnych składników COM i bibliotek DLL.

Środowisko wykonawcze jest przeznaczone do zwiększenia wydajności. Chociaż środowisko uruchomieniowe języka wspólnego udostępnia wiele standardowych usług czasu wykonywania, kod zarządzany nigdy nie jest interpretowany. Funkcja o nazwie just-in-time (JIT) kompilacja umożliwia wszystkich zarządzanych uruchamianie kodu w macierzystym języku maszyny, systemu, na którym jest wykonywany. W międzyczasie Menedżer pamięci eliminuje ewentualność fragmentacji pamięci i zwiększa pamięci miejscowość odniesienia do dalszego zwiększenia wydajności.

Wreszcie środowisko wykonawcze może być obsługiwany przez aplikacje o wysokiej wydajności, po stronie serwera, takie jak Microsoft SQL Server i usług Internet Information Services (IIS). Infrastruktura ta umożliwia zapisanie logiki biznesowej, a przy tym nadal najwyższej wydajności w branży najlepsze serwerów korporacyjnych, obsługujących hosta runtime przy użyciu kodu zarządzanego.

## <a name="net-framework-class-library"></a>Biblioteka klas programu .NET Framework

Biblioteka klas .NET Framework jest kolekcją typów wielokrotnego użytku, które są ściśle zintegrowane ze środowiska uruchomieniowego języka wspólnego. Biblioteka klas jest zorientowana obiektowo, zapewniając typy, z której wywodzi się funkcji we własnym kodzie zarządzanym. To nie tylko sprawia, że typy programu .NET Framework jest łatwa w użyciu, ale również skraca czas związany z poznawaniem nowych funkcji programu .NET Framework. Ponadto składników innych firm bezproblemowo integrować z klas w programie .NET Framework.

Na przykład klas kolekcji .NET Framework implementują zbiór interfejsów do tworzenia własnych klas kolekcji. Twoje klasy kolekcji mieszają się niezauważalnie z klasami W.NET Framework.

Jak można oczekiwać od biblioteki klas obiektowych, typy programu .NET Framework umożliwiają wykonywanie szeregu typowych zadań programistycznych, w tym zadań takich jak zarządzanie ciągami, zbieranie danych, łączność z bazą danych i uzyskiwania dostępu do plików. Oprócz tych wspólnych zadań Biblioteka klas zawiera typy, które obsługują wiele specjalistycznych scenariuszy projektowych. Użyj programu .NET Framework do tworzenia następujących typów aplikacji i usług:

- Aplikacje konsoli. Zobacz [Kompilowanie aplikacji konsoli](../../../docs/standard/building-console-apps.md).

- Windows aplikacje graficznego interfejsu użytkownika (Windows Forms). Zobacz [Windows Forms](../../../docs/framework/winforms/index.md).

- Windows Presentation Foundation (WPF) aplikacji. Zobacz [Windows Presentation Foundation](../../../docs/framework/wpf/index.md).

- Aplikacje platformy ASP.NET. Zobacz [aplikacje ASP.NET sieci Web](../../../docs/framework/develop-web-apps-with-aspnet.md).

- Usługi systemu Windows. Zobacz [wprowadzenie do Windows usługi aplikacji](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md).

- Aplikacje zorientowane na usługę przy użyciu usługi Windows Communication Foundation (WCF). Zobacz [zorientowane na usługę aplikacje z usługą WCF](../../../docs/framework/wcf/index.md).

- Aplikacje współdziałające z przepływu pracy przy użyciu Windows Workflow Foundation (WF). Zobacz [Windows Workflow Foundation](../windows-workflow-foundation/index.md).

Klas formularzy Windows są kompleksowymi zestawami typów wielokrotnego użytku, które znacznie upraszczają proces tworzenia graficznego interfejsu użytkownika Windows. Jeśli piszesz aplikację formularza sieci Web platformy ASP.NET, można użyć klas formularzy sieci Web.

## <a name="see-also"></a>Zobacz także

- [Wymagania systemowe](../../../docs/framework/get-started/system-requirements.md)
- [Przewodnik instalacji](../../../docs/framework/install/index.md)
- [Podręcznik programowania](../../../docs/framework/development-guide.md)
- [Narzędzia](../../../docs/framework/tools/index.md)
- [Samouczki i przykłady kodu platformy .NET](../../samples-and-tutorials/index.md)
- [Biblioteka klas programu .NET framework](https://go.microsoft.com/fwlink/?LinkID=227195)
