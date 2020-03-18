---
title: Co to jest kod zarządzany?
description: Dowiedz się, jak kod zarządzany jest kod, którego wykonanie jest zarządzane przez czas wykonywania, common language runtime (CLR).
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 9133859bd9c999e076effcf0d4d631c59db02f33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "61910120"
---
# <a name="what-is-managed-code"></a>Co to jest „kod zarządzany”?

Podczas pracy z .NET Framework często można napotkać termin "kod zarządzany". W tym dokumencie wyjaśniono, co oznacza ten termin i dodatkowe informacje wokół niego.

Mówiąc prościej, kod zarządzany jest tylko, że: kod, którego wykonanie jest zarządzane przez czas wykonywania. W takim przypadku czas wykonywania, o której mowa jest nazywany **Common Language Runtime** lub CLR, niezależnie od implementacji[(Mono](https://www.mono-project.com/) lub .NET Framework lub .NET Core). Clr jest odpowiedzialny za pobranie kodu zarządzanego, skompilowanie go do kodu maszynowego, a następnie jego wykonanie. Ponadto czas wykonywania zapewnia kilka ważnych usług, takich jak automatyczne zarządzanie pamięcią, granice zabezpieczeń, bezpieczeństwo typów itp.

Kontrast to do sposobu, w jaki można uruchomić program C/C++, zwany także "kod niezarządzany". W niezarządzanym świecie programista jest odpowiedzialny za prawie wszystko. Rzeczywisty program jest zasadniczo binarny, że system operacyjny (OS) ładuje się do pamięci i uruchamia. Wszystko inne, od zarządzania pamięcią po względy bezpieczeństwa, jest obciążeniem programisty.

Kod zarządzany jest napisany w jednym z języków wysokiego poziomu, które mogą być uruchamiane na wierzchu .NET, takich jak C#, Visual Basic, F# i innych. Podczas kompilowania kodu napisanego w tych językach z ich odpowiedniego kompilatora, nie otrzymasz kodu maszynowego. Otrzymasz kod **języka pośredniego,** który w czasie wykonywania następnie kompiluje i wykonuje. C++ jest jedynym wyjątkiem od tej reguły, ponieważ może również tworzyć natywne, niezarządzane pliki binarne uruchamiane w systemie Windows.

## <a name="intermediate-language--execution"></a>Wykonywanie & języka pośredniego

Co to jest "Język pośredni" (lub IL w skrócie)? Jest to produkt kompilacji kodu napisanego w językach .NET wysokiego poziomu. Po skompilowania kodu napisanego w jednym z tych języków, otrzymasz binarny, który jest wykonany z IL. Należy pamiętać, że IL jest niezależna od określonego języka, który działa na górze czasu wykonywania; istnieje nawet oddzielna specyfikacja dla niego, że można przeczytać, jeśli jesteś tak skłonny.

Po wyprodukowaniu IL z kodu wysokiego poziomu, najprawdopodobniej będziesz chciał go uruchomić. To jest, gdy CLR przejmuje i rozpoczyna proces **just-in-time** kompilacji lub **JIT-ing** kodu z IL do kodu maszynowego, które faktycznie mogą być uruchamiane na procesorze. W ten sposób CLR dokładnie wie, co robi kod i może skutecznie _nim zarządzać._

Język pośredni jest czasami nazywany również wspólnym językiem pośrednim (CIL) lub Microsoft Intermediate Language (MSIL).

## <a name="unmanaged-code-interoperability"></a>Współdziałanie kodu niezarządzanego

Oczywiście CLR umożliwia przekazywanie granic między zarządzanym i niezarządzanym świecie, a istnieje wiele kodu, który to robi, nawet w [bibliotekach klas podstawowych](framework-libraries.md). Nazywa się to **interoperacyjnością** lub po prostu **w skrócie.** Przepisy te umożliwiają na przykład zawinięcie biblioteki niezarządzanej i wywołanie jej. Jednak należy pamiętać, że po wykonaniu tej pracy, gdy kod przekazuje granice czasu wykonywania, rzeczywiste zarządzanie wykonaniem jest ponownie w ręku kodu niezarządzanego, a zatem podlega tym samym ograniczeniom.

Podobne do tego C# jest jeden język, który umożliwia użycie konstrukcji niezarządzanych, takich jak wskaźniki bezpośrednio w kodzie, przy użyciu tak **zwanych niebezpiecznych kontekstu,** który wyznacza fragment kodu, dla którego wykonanie nie jest zarządzany przez CLR.

## <a name="more-resources"></a>Więcej zasobów

* [Przegląd programu .NET Framework](../framework/get-started/overview.md)
* [Niebezpieczny kod i wskaźniki](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
* [Natywna interoperacyjność](./native-interop/index.md)
