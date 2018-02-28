---
title: "Roslyn analizatorów — na podstawie .NET"
description: "Więcej informacji na temat analizatorów Roslyn na podstawie, znaleźć problemy, które sugeruje rozwiązania tych problemów."
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a>Analizatory na podstawie Roslyn

Na podstawie Roslyn analizatorów umożliwia analizowanie kodu źródłowego projektu, aby znaleźć problemy i zaproponuje poprawki zestawu .NET SDK kompilatora (Roslyn API). Różne analizatorów poszukaj różne rodzaje problemów, począwszy od rozwiązania, które mogą spowodować usterki do zagadnienia dotyczące zabezpieczeń w celu zgodności z interfejsu API.

Na podstawie Roslyn analizatorów działa zarówno interakcyjne i podczas kompilacji. Analizatora znajdują się różne wskazówki w Visual Studio lub w kompilacji z wiersza polecenia.

Podczas edytowania kodu w programie Visual Studio analizatorów Uruchom jako wprowadzić zmiany, przechwytywanie możliwych problemach, jak tworzyć kod wyzwolenia problemy. Wszystkie problemy zostały wyróżnione z zygzaki w jakikolwiek problem. Żarówka Wyświetla programu Visual Studio, a po jego kliknięciu analizatora sugeruje możliwe rozwiązania tego problemu. Podczas kompilowania projektu programu Visual Studio lub z wiersza polecenia analizy kodu źródłowego i analizatora zawiera pełną listę potencjalnych problemów. Na poniższej ilustracji przedstawiono przykład.

![problemy zgłoszone przez analizator framework](./media/framework-analyzers-2.png)

Na podstawie Roslyn analizatorów raport potencjalnych problemach, jak błędy, ostrzeżenia lub informacji na podstawie ich wagi problemu.

Na podstawie Roslyn analizatorów jest instalowany jako pakietów NuGet w projekcie. Skonfigurowany analizatorów wszystkie ustawienia dla każdego analizatora przywrócona i uruchomić na maszynie Każdy deweloper dla tego projektu.

> [!NOTE]
> Środowisko użytkownika na podstawie Roslyn analizatorów jest inny niż z biblioteki analizy kodu, takich jak starszych wersji programu FxCop oraz narzędzia do analizy zabezpieczeń.  Nie trzeba uruchomić na podstawie Roslyn analizatorów. Nie istnieje potrzeba użycie elementów menu "Uruchom analizę kodu" w menu "Analyze" w programie Visual Studio. Na podstawie Roslyn analizatorów Uruchom asychronously podczas pracy. 

## <a name="more-information-on-specific-analyzers"></a>Więcej informacji na temat określonych analizatorów

Następujące analizatorów zostały omówione w tej sekcji:

[Analizator interfejsu API](api-analyzer.md): ten analyzer sprawdza, czy kod dla potencjalnych zagrożeń zgodności lub korzysta z interfejsów API przestarzałe.    
[Analizator Framework](framework-analyzer.md): ten analyzer sprawdza swój kod, aby upewnić się, wynika z wytycznymi dla aplikacji .NET Framework. Reguły obejmują kilka zabezpieczeń na podstawie zalecenia.
