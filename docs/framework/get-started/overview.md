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
ms.openlocfilehash: c7a3548cb0d7e841f32824eda52565e64279536e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052001"
---
# <a name="overview-of-the-net-framework"></a>Przegląd programu .NET Framework

.NET Framework to technologia, która obsługuje Kompilowanie i uruchamianie nowej generacji aplikacji i usług sieci Web XML. .NET Framework zaprojektowano w celu spełnienia następujących celów:

- Zapewnianie spójnego zorientowanego obiektowo środowiska programowania, niezależnie od tego, czy kod obiektu jest przechowywany i wykonywany lokalnie, wykonywany lokalnie, ale dystrybuowany z Internetu czy wykonywany zdalnie.

- Zapewnienie środowiska wykonania kodu, które minimalizuje konflikty wdrażania oprogramowania i przechowywania wersji.

- Aby zapewnić środowisko wykonywania kodu, które wspiera bezpieczne wykonywanie kodu, w tym kod utworzony przez nieznaną lub częściowo zaufaną stronę trzecią.

- Zapewnienie środowiska wykonania kodu, które eliminuje problemy z wydajnością w środowiskach ze skryptami lub interpretowane.

- Aby zapewnić spójność dla deweloperów w różnych różnych typach aplikacji, takich jak aplikacje oparte na systemie Windows i aplikacje oparte na sieci Web.

- Aby utworzyć całą komunikację z normami branżowymi w celu zapewnienia, że kod oparty na .NET Framework integruje się z jakimkolwiek innym kodem.

> [!NOTE]
> Aby uzyskać ogólne wprowadzenie do .NET Framework dla użytkowników i deweloperów, zobacz [wprowadzenie](index.md).

.NET Framework składa się ze środowiska uruchomieniowego języka wspólnego (CLR) i biblioteki klas .NET Framework. Środowisko uruchomieniowe języka wspólnego jest podstawą .NET Framework. Należy traktować środowisko uruchomieniowe jako agenta, który zarządza kodem w czasie wykonywania, zapewniającym podstawowe usługi, takie jak zarządzanie pamięcią, zarządzanie wątkami i komunikacja zdalna, a także wymuszanie ścisłego bezpieczeństwa typów i inne formy dokładności kodu, które promują bezpieczeństwo i niezawodność. W rzeczywistości koncepcja zarządzania kodem jest podstawową zasadą środowiska uruchomieniowego. Kod przeznaczony dla środowiska uruchomieniowego jest znany jako kod zarządzany, podczas gdy kod, który nie jest celem środowiska uruchomieniowego, jest znany jako kod niezarządzany. Biblioteka klas to kompleksowa, zorientowana obiektowo Kolekcja typów wielokrotnego użytku, które służą do opracowywania aplikacji w oparciu o tradycyjne aplikacje wiersza polecenia lub graficznego interfejsu użytkownika (GUI) do aplikacji na podstawie najnowszych innowacji oferowanych przez ASP.NET, takich jak sieć Web Formularze i usługi sieci Web XML.

.NET Framework mogą być hostowane przez składniki niezarządzane, które ładują środowisko uruchomieniowe języka wspólnego do ich procesów i inicjują wykonywanie kodu zarządzanego, tworząc w ten sposób środowisko oprogramowania korzystające z funkcji zarządzanych i niezarządzanych. .NET Framework zawiera nie tylko kilka hostów środowiska uruchomieniowego, ale również obsługuje opracowywanie hostów środowiska uruchomieniowego innych firm.

Na przykład ASP.NET hostuje środowisko uruchomieniowe w celu zapewnienia skalowalnego środowiska po stronie serwera dla kodu zarządzanego. ASP.NET działa bezpośrednio w środowisku uruchomieniowym w celu włączenia aplikacji ASP.NET i usług sieci Web XML, które zostały omówione w dalszej części tego tematu.

Internet Explorer to przykład niezarządzanej aplikacji, która hostuje środowisko uruchomieniowe (w postaci rozszerzenia typu MIME). Korzystanie z programu Internet Explorer do hostowania środowiska uruchomieniowego umożliwia osadzanie składników zarządzanych lub formantów Windows Forms w dokumentach HTML. Hosting środowiska uruchomieniowego w ten sposób sprawia, że zarządzany kod mobilny jest możliwy, ale z znaczącymi ulepszeniami, które są dostępne tylko w przypadku ofert z kodem zarządzanym, takich jak wykonywanie częściowo zaufane i izolowany magazyn plików.

Na poniższej ilustracji przedstawiono relacje środowiska uruchomieniowego języka wspólnego i biblioteki klas z aplikacjami oraz do całego systemu. Ilustracja pokazuje również, jak kod zarządzany działa w ramach większej architektury.

![Zrzut ekranu pokazujący, jak kod zarządzany działa w ramach większej architektury.](./media/overview/language-runtime-class-library-relationship.gif)

W poniższych sekcjach szczegółowo opisano główne funkcje .NET Framework.

## <a name="features-of-the-common-language-runtime"></a>Funkcje środowiska uruchomieniowego języka wspólnego

Środowisko uruchomieniowe języka wspólnego zarządza pamięcią, wykonywaniem wątków, wykonywaniem kodu, weryfikacją bezpieczeństwa kodu, kompilacją i innymi usługami systemowymi. Te funkcje są wewnętrzne dla kodu zarządzanego, który jest uruchamiany w środowisku uruchomieniowym języka wspólnego.

W odniesieniu do zabezpieczeń zarządzane składniki są przyznawane różnym stopniu zaufania, w zależności od różnych czynników, które obejmują ich źródła (takie jak Internet, Sieć przedsiębiorstwa lub komputer lokalny). Oznacza to, że zarządzany składnik może lub może nie być w stanie wykonywać operacji dostępu do plików, operacji dostępu do rejestru ani innych poufnych funkcji, nawet jeśli jest używany w tej samej aktywnej aplikacji.

Środowisko uruchomieniowe wymusza również niezawodność kodu przez implementację infrastruktury ścisłej weryfikacji typu i kodu o nazwie system typu wspólnego (CTS). CTS gwarantuje, że cały kod zarządzany jest własny opis. Różne kompilatory języka firmy Microsoft i innych firm generują kod zarządzany, który jest zgodny z CTS. Oznacza to, że kod zarządzany może zużywać inne zarządzane typy i wystąpienia, jednocześnie jednocześnie wymuszające wierność i bezpieczeństwo typów.

Ponadto zarządzane środowisko uruchomieniowe programu eliminuje wiele typowych problemów z oprogramowaniem. Na przykład środowisko uruchomieniowe automatycznie obsługuje układ obiektu i zarządza odwołaniami do obiektów, zwalniając je, gdy nie są już używane. To automatyczne zarządzanie pamięcią rozwiązuje dwa najczęstsze błędy aplikacji, przecieki pamięci i nieprawidłowe odwołania do pamięci.

Środowisko uruchomieniowe przyspiesza również produktywność deweloperów. Na przykład programiści piszą aplikacje w ich języku programistycznym, ale w pełni wykorzystują środowisko uruchomieniowe, bibliotekę klas oraz składniki pisane w innych językach przez innych deweloperów. Każdy dostawca kompilatora, który wybiera cel środowiska uruchomieniowego, może to zrobić. Kompilatory języka, które są przeznaczone dla .NET Framework sprawiają, że funkcje .NET Framework są dostępne dla istniejącego kodu pisanego w tym języku, znacznie przyspieszają proces migracji istniejących aplikacji.

Środowisko uruchomieniowe jest przeznaczone dla oprogramowania w przyszłości, ale również obsługuje oprogramowanie z dzisiaj i wczoraj. Współdziałanie między kodem zarządzanym i niezarządzanym pozwala deweloperom nadal korzystać z niezbędnych składników COM i bibliotek DLL.

Środowisko uruchomieniowe zostało zaprojektowane w celu zwiększenia wydajności. Chociaż środowisko uruchomieniowe języka wspólnego udostępnia wiele standardowych usług czasu wykonywania, kod zarządzany nigdy nie jest interpretowany. Funkcja, która nazywa kompilację just-in-Time (JIT), umożliwia uruchamianie całego kodu zarządzanego w języku macierzystym systemu, w którym jest wykonywane. W tym czasie Menedżer pamięci usuwa możliwości fragmentacji pamięci i zwiększa ilość pamięci w odwołaniu, aby zwiększyć wydajność.

Na koniec środowisko uruchomieniowe może być hostowane przez aplikacje po stronie serwera, takie jak Microsoft SQL Server i Internet Information Services (IIS). Ta infrastruktura umożliwia korzystanie z kodu zarządzanego do pisania logiki biznesowej, przy jednoczesnym zachowaniu najwyższej wydajności najlepszych serwerów przedsiębiorstwa, które obsługują hosting w czasie wykonywania.

## <a name="net-framework-class-library"></a>Biblioteka klas programu .NET Framework

Biblioteka klas .NET Framework jest kolekcją typów wielokrotnego użytku, które są ściśle zintegrowane ze środowiskiem uruchomieniowym języka wspólnego. Biblioteka klas jest zorientowana obiektowo, dostarczając typy, z których pochodzi własny kod zarządzany. To nie tylko ułatwia używanie typów .NET Framework, ale również skraca czas związany z uczeniem nowych funkcji .NET Framework. Ponadto składniki innych firm integrują się bezproblemowo z klasami w .NET Framework.

Na przykład klasy kolekcji .NET Framework implementują zestaw interfejsów do tworzenia własnych klas kolekcji. Klasy kolekcji mieszają się bezproblemowo z klasami w .NET Framework.

Zgodnie z oczekiwaniami z biblioteki klas zorientowanej obiektowo typy .NET Framework umożliwiają wykonywanie wielu typowych zadań programistycznych, w tym zadań, takich jak zarządzanie ciągami, zbieranie danych, łączność z bazą danych i dostęp do plików. Oprócz tych typowych zadań Biblioteka klas zawiera typy, które obsługują różne wyspecjalizowane scenariusze programistyczne. Użyj .NET Framework, aby opracowywać następujące typy aplikacji i usług:

- Aplikacje konsolowe. Zobacz [Kompilowanie aplikacji konsolowych](../../standard/building-console-apps.md).

- Aplikacje GUI systemu Windows (Windows Forms). Zobacz [Windows Forms](../winforms/index.md).

- Aplikacje Windows Presentation Foundation (WPF). Zobacz [Windows Presentation Foundation](../wpf/index.md).

- Aplikacje ASP.NET. Zobacz [aplikacje sieci Web za pomocą ASP.NET](../develop-web-apps-with-aspnet.md).

- Usługi systemu Windows. Zobacz [wprowadzenie do aplikacji usług systemu Windows](../windows-services/introduction-to-windows-service-applications.md).

- Aplikacje zorientowane na usługę korzystające z Windows Communication Foundation (WCF). Zobacz [aplikacje zorientowane na usługę za pomocą programu WCF](../wcf/index.md).

- Aplikacje obsługujące przepływy pracy korzystające z Windows Workflow Foundation (WF). Zobacz [Windows Workflow Foundation](../windows-workflow-foundation/index.md).

Klasy Windows Forms to kompleksowy zestaw typów wielokrotnego użytku, które znacznie upraszczają tworzenie interfejsu GUI systemu Windows. Jeśli piszesz aplikację formularza sieci Web ASP.NET, możesz użyć klas formularzy sieci Web.

## <a name="see-also"></a>Zobacz także

- [Wymagania systemowe](system-requirements.md)
- [Przewodnik instalacji](../install/index.md)
- [Podręcznik programowania](../development-guide.md)
- [Narzędzia](../tools/index.md)
- [Przykłady i samouczki dotyczące platformy .NET](../../samples-and-tutorials/index.md)
- [Biblioteka klas .NET Framework](https://go.microsoft.com/fwlink/?LinkID=227195)
