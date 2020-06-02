---
title: Co to jest kod zarządzany?
description: Dowiedz się, w jaki sposób kod zarządzany jest kodem, którego wykonywanie jest zarządzane przez środowisko uruchomieniowe, środowisko uruchomieniowe języka wspólnego (CLR).
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 2d89fd48e4c05dc7ec7c27846a3580ee36b1886f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290087"
---
# <a name="what-is-managed-code"></a>Co to jest „kod zarządzany”?

Podczas pracy z .NET Framework często występuje termin "kod zarządzany". W tym dokumencie wyjaśniono, czym jest ten termin, i dodatkowe informacje.

Aby to zrobić bardzo proste, kod zarządzany jest tylko taki: kod, którego wykonywanie jest zarządzane przez środowisko uruchomieniowe. W takim przypadku środowisko uruchomieniowe jest nazywane środowiskiem **uruchomieniowym języka wspólnego** lub CLR niezależnie od implementacji ([mono](https://www.mono-project.com/) lub .NET Framework lub .NET Core). Środowisko CLR jest odpowiedzialne za pobieranie kodu zarządzanego, kompilowanie go do kodu maszynowego i wykonywanie go. Na początku środowisko uruchomieniowe zapewnia kilka ważnych usług, takich jak automatyczne zarządzanie pamięcią, granice zabezpieczeń, bezpieczeństwo typów itp.

Z drugiej strony, tak jak w przypadku uruchamiania programu C/C++, nazywanego również "niezarządzanym kodem". Na świecie niezarządzanym programista jest odpowiedzialny za całkiem wiele rzeczy. Rzeczywisty program to zasadniczo plik binarny, który system operacyjny (OS) ładuje do pamięci i zacznie działać. Wszystkie inne elementy, od zarządzania pamięcią do zagadnień związanych z bezpieczeństwem, są ciężarem programisty.

Kod zarządzany jest zapisywana w jednym z języków wysokiego poziomu, które można uruchamiać na platformie .NET, takich jak C#, Visual Basic, F # i innych. Podczas kompilowania kodu pisanego w tych językach przy użyciu odpowiedniego kompilatora nie otrzymujesz kodu maszynowego. Uzyskujesz kod **języka pośredniego** , który następnie środowisko uruchomieniowe kompiluje i wykonuje. C++ jest jedynym wyjątkiem od tej reguły, ponieważ może również generować natywne, niezarządzane pliki binarne działające w systemie Windows.

## <a name="intermediate-language--execution"></a>Wykonanie & języka pośredniego

Co to jest "język pośredni" (lub IL na krótko)? Jest to produkt, który jest przeznaczony do kompilowania kodu pisanego w językach .NET wysokiego poziomu. Po skompilowaniu kodu w jednym z tych języków otrzymasz plik binarny, który został utworzony z IL. Należy pamiętać, że IL jest niezależna od dowolnego języka, który działa w środowisku uruchomieniowym; Istnieje również odrębna Specyfikacja, którą można odczytać w przypadku, gdy jest to możliwe.

Po utworzeniu języka IL z poziomu kodu wysokiego poziomu najprawdopodobniej chcesz go uruchomić. Jest to miejsce, w którym środowisko CLR przejmuje i uruchamia proces kompilowania **just-in-Time** lub **JIT-** przetwarza kod z Il do kodu maszynowego, który można faktycznie uruchomić na procesorze. W ten sposób środowisko CLR wie dokładnie, co robi kod i może efektywnie _zarządzać_ nim.

Język pośredni jest czasami nazywany również typowym językiem pośrednim (CIL) lub językiem pośrednim firmy Microsoft (MSIL).

## <a name="unmanaged-code-interoperability"></a>Współdziałanie kodu niezarządzanego

Oczywiście środowisko CLR umożliwia przekazywanie granic między zarządzanym i niezarządzanym światem, a istnieje dużo kodu, który robi, nawet w [bibliotekach klas bazowych](framework-libraries.md). Jest to tzw. interoperacyjność **lub tylko** **niedziałanie** . Te postanowienia pozwolą na przykład zawinąć niezarządzaną bibliotekę i wywołać ją. Należy jednak pamiętać, że po wykonaniu tej czynności, gdy kod przekaże granice środowiska uruchomieniowego, rzeczywiste Zarządzanie wykonywaniem jest ponownie dostępne w odróżnieniu od kodu niezarządzanego i w ten sposób znajduje się w tych samych ograniczeniach.

Podobnie jak w przypadku języka C# jest to jeden język, który umożliwia korzystanie z niezarządzanych konstrukcji, takich jak wskaźniki bezpośrednio w kodzie, przy użyciu co jest znane jako **niebezpieczny kontekst** , który wyznacza fragment kodu, dla którego wykonywanie nie jest zarządzane przez środowisko CLR.

## <a name="more-resources"></a>Dodatkowe zasoby

* [Przegląd programu .NET Framework](../framework/get-started/overview.md)
* [Niebezpieczny kod i wskaźniki](../csharp/programming-guide/unsafe-code-pointers/index.md)
* [Współdziałanie natywne](./native-interop/index.md)
