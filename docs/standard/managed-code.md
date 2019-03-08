---
title: Co to jest zarządzany kod?
description: Dowiedz się, jak zarządzany kod jest kodem, których wykonanie jest zarządzany przez środowisko uruchomieniowe, środowisko uruchomieniowe języka wspólnego (CLR).
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 9133859bd9c999e076effcf0d4d631c59db02f33
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678761"
---
# <a name="what-is-managed-code"></a>Co to jest "kod zarządzany"?

Podczas pracy z programem .NET Framework, można napotkać często termin "kod zarządzany". W tym dokumencie wyjaśniono, co oznacza ten termin i dodatkowe informacje na temat jej.

Aby przełączyć bardzo prosty sposób, kod zarządzany jest po prostu: kodu, których wykonanie jest zarządzany przez środowisko uruchomieniowe. W tym przypadku danego środowiska uruchomieniowego jest nazywany **środowiska uruchomieniowego języka wspólnego** lub CLR, niezależnie od implementacji ([Mono](https://www.mono-project.com/) lub .NET Framework lub .NET Core). Środowisko CLR jest odpowiedzialny za wykonanie kodu zarządzanego, kompilując go do kodu maszynowego i jej wykonanie. Na górze, środowisko wykonawcze zapewnia kilka ważnych usług, takich jak automatyczne zarządzanie pamięcią, granice zabezpieczeń wpisz bezpieczeństwa itp.

Natomiast to sposób, który należy uruchomić program C/C++, nazywany również "Kod niezarządzanego". W świecie niezarządzanych programistę odpowiada za niemal wszystkie elementy. Rzeczywisty program jest zasadniczo plik binarny, który jest ładowany do pamięci systemu operacyjnego (OS) i uruchamia. Wszystkie inne czynności, od zarządzania pamięci do zagadnienia dotyczące zabezpieczeń są obciążenia programisty.

Kod zarządzany jest zapisywany w jednym z języków wysokiego poziomu, które mogą być uruchamiane na szczycie .NET, takich jak C#, Visual Basic F# i innym osobom. Podczas kompilowania kodu napisanego w tych językach za pomocą ich odpowiednich kompilatora nie uzyskasz kodu maszynowego. Możesz uzyskać **języka pośredniego** kod, który środowiska uruchomieniowego następnie kompiluje i wykonuje. Język C++ jest jedynym wyjątkiem od tej reguły, jak można utworzyć również natywnych i niezarządzane pliki binarne, które systemem Windows.

## <a name="intermediate-language--execution"></a>Pośredni języka i wykonywanie

Co to jest "Język pośredni" (lub IL w skrócie)? Jest to produkt kompilacji kod napisany w językach .NET wysokiego poziomu. Po skompilowaniu kodu napisanego w jeden z tych języków, zostanie wyświetlony plik binarny, który składa się z IL. Ważne jest, aby pamiętać, że IL jest niezależna od określonego języka, uruchamiane w systemie środowiska uruchomieniowego; jest parzysta oddzielnych specyfikacji dla niego, który może odczytać, jeśli jest więc pochylone.

Gdy zostanie wyświetlony IL w kodzie wysokiego poziomu, prawdopodobnie można go uruchomić. Jest to, gdzie CLR przejmuje i rozpoczyna proces **Just-In-Time** kompilacji, lub **JIT ing** kod z IL do kodu maszynowego, który faktycznie można uruchomić na procesorze CPU. W ten sposób CLR wie dokładnie co kod robi i może się skutecznie _zarządzanie_ go.

Język pośredni czasami skrót wspólny język pośredni (CIL) lub Microsoft Intermediate Language (MSIL).

## <a name="unmanaged-code-interoperability"></a>Współdziałanie kodu niezarządzanego

Oczywiście, CLR umożliwia przekazywanie granice między zarządzanymi i niezarządzanymi świecie i jest dużo kod, który obsługuje, nawet w [bibliotek klas Base](framework-libraries.md). Jest to nazywane **współdziałanie** lub po prostu **interop** w skrócie. Te przepisy pozwoliłoby, na przykład zawinąć biblioteką niezarządzaną i wywoływać ją. Jednak należy pamiętać, że gdy to zrobisz, gdy kod przekazuje granice środowiska uruchomieniowego, rzeczywiste Zarządzanie wykonywania ponownie jest ręczne niezarządzanego kodu i związku z tym podlega tym samym ograniczeniom.

Mniej więcej tak, C# to jeden język, który pozwala na używanie niezarządzanych konstrukcji, takich jak wskaźniki bezpośrednio w kodzie, wykorzystując, co jest nazywane **niebezpieczny kontekst** który wyznacza fragment kodu, dla którego wykonanie nie jest zarządzany przez środowisko CLR.

## <a name="more-resources"></a>Inne zasoby

* [Omówienie programu .NET Framework](../framework/get-started/overview.md)
* [Niebezpieczny kod i wskaźniki](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
* [Współdziałanie natywne](./native-interop/index.md)
