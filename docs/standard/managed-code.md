---
title: Co to jest zarządzany kod?
description: Dowiedz się, jak zarządzanego kodu jest kodem, których wykonanie jest zarządzany przez moduł wykonawczy środowiska uruchomieniowego języka wspólnego (CLR).
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 46bbe30f216ba9b0a3bc7f88267c428ec56de614
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="what-is-managed-code"></a>Co to jest "kodu zarządzanego"?

Podczas pracy z .NET Framework, można napotkać często termin "kod zarządzany". Ten dokument zostanie Wyjaśnij, określenie to oznacza i dodatkowe informacje wokół niego.

Aby umieścić bardzo prosty, kod zarządzany jest właśnie tę: kodu, których wykonanie jest zarządzane przez środowisko wykonawcze. W takim przypadku nosi nazwę środowiska uruchomieniowego w **środowisko uruchomieniowe języka wspólnego** lub CLR, niezależnie od implementacji ([Mono](https://www.mono-project.com/) lub .NET Framework lub .NET Core). CLR jest odpowiedzialny za pobierania kodu zarządzanego, kompilowanie go do kod maszynowy i jej wykonanie. U góry, runtime zawiera kilka ważnych usług, takich jak automatyczne zarządzanie pamięcią, granic zabezpieczeń typu bezpieczeństwa itp.

Natomiast to sposób którą należy uruchomić program C/C++, nazywane również "kodu niezarządzanego". W świecie niezarządzane programistę jest odpowiedzialny za niemal wszystkie elementy. Rzeczywiste program jest zasadniczo binary, który system operacyjny (OS) ładuje do pamięci i uruchamia. Wszystkie inne z zarządzania pamięci do zagadnienia dotyczące zabezpieczeń są obciążenia programisty.

Zarządzany kod jest zapisywany w jednym z języków wysokiego poziomu, które mogą być uruchamiane na górze .NET, takich jak C#, Visual Basic, F # i inne. Podczas kompilowania kodu napisanego w tych językach z ich odpowiednich kompilatora nie otrzymasz kod maszynowy. Możesz uzyskać **język pośredni** środowiska uruchomieniowego następnie kompiluje i uruchamia kod. C++ jest jedynym wyjątkiem od tej reguły, jak można utworzyć również macierzystego, niezarządzane pliki binarne, uruchomionych w systemie Windows.

## <a name="intermediate-language--execution"></a>Pośredni języka i wykonanie

Co to jest "Język pośredni" (lub IL skrócie)? Jest to produkt kompilacji kod napisany w językach .NET wysokiego poziomu. Możesz kompilacji kodu napisane w jeden z tych języków, otrzymasz pliku binarnego, które zostało utworzone poza IL. Ważne jest, aby należy pamiętać, że IL jest niezależna od dowolnego określonego języka, który działa w oparciu o środowiska uruchomieniowego; nawet to oddzielne Specyfikacja dla niego, który może odczytywać, jeśli jest to pochylone.

Gdy utworzysz IL w kodzie wysokiego poziomu, prawdopodobnie można go uruchomić. Gdzie CLR przejmuje i uruchamia proces **Just In Time** kompilowania, lub **używać JIT** kodu z IL do kodu maszyny, który faktycznie można uruchamiać na procesora CPU. W ten sposób CLR zna dokładnie kodu czynności i mogą skutecznie _zarządzanie_ go.

Język pośredni również czasami jest nazywany wspólnego języka pośredniego (CIL) lub Microsoft języka pośredniego (MSIL).

## <a name="unmanaged-code-interoperability"></a>Współdziałanie z kodem niezarządzanym

Oczywiście CLR umożliwia przekazywanie granice między world zarządzane i niezarządzane, a wiele kod, który obsługuje, nawet w [podstawowej biblioteki klas](framework-libraries.md). Ta metoda jest wywoływana **współdziałanie** lub po prostu **interop** skrócie. Umożliwia te przepisy, na przykład dobiega końca niezarządzane biblioteki i wywołują go. Jest jednak należy pamiętać, że po tym, gdy kod przekazuje granice środowiska uruchomieniowego rzeczywiste Zarządzanie wykonywania jest ponownie ręczne kodu niezarządzanego, a w związku z tym podlega takie same ograniczenia.

Podobnie do poniższego, C# jest jeden język, który pozwala na stosowanie konstrukcji niezarządzanych, takich jak wskaźniki bezpośrednio w kodzie wykorzystując, co jest nazywane **niebezpiecznym kontekście** który wyznacza fragment kodu, dla którego wykonanie nie jest zarządzany przez CLR.

## <a name="more-resources"></a>Więcej zasobów

*   [Omówienie pojęć programu .NET framework](https://msdn.microsoft.com/library/zw4w595w.aspx)
*   [Niebezpieczny kod i wskaźniki](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
*   [Współdziałanie (Przewodnik programowania C#)](https://msdn.microsoft.com/library/ms173184.aspx)
