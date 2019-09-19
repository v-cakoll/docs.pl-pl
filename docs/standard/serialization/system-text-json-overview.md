---
title: Serializacja kodu JSON w programie .NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 6cb45fded220b6123dbf4461f5f1cf1c3556ff69
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083092"
---
# <a name="json-serialization-in-net"></a>Serializacja kodu JSON w programie .NET

`System.Text.Json` Przestrzeń nazw zawiera funkcje serializowania do i z JavaScript Object Notation (JSON).

Projekt biblioteki wyróżnia wysoką wydajność i małą alokację pamięci w ramach rozbudowanego zestawu funkcji. Wbudowana obsługa UTF-8 optymalizuje proces odczytywania i pisania tekstu JSON zakodowanego w formacie UTF-8, który jest najbardziej rozpowszechnionym kodowaniem danych w sieci Web i plikach na dysku.

Biblioteka zawiera również klasy umożliwiające pracę z modelem DOM (Document objecting) w pamięci. Ta funkcja włącza losowy dostęp tylko do odczytu do elementów w pliku JSON lub ciągu. 

## <a name="how-to-get-the-library"></a>Jak uzyskać bibliotekę

* Biblioteka jest wbudowana w ramach platformy udostępnionej [.NET Core 3,0](https://aka.ms/netcore3download) .
* W przypadku innych platform docelowych Zainstaluj pakiet NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) . Pakiet obsługuje:
  * .NET Standard 2,0 i nowsze wersje
  * .NET Framework 4,61 i nowsze wersje
  * .NET Core 2,0 i nowsze wersje

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Jak używać biblioteki](system-text-json-how-to.md)
* [Kod źródłowy](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [Dokumentacja interfejsu API](xref:System.Text.Json)
* [Plan rozwoju](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* Problemy z usługą GitHub w repozytorium dotnet/corefx
  * [Omówienie tworzenia pliku System. Text. JSON](https://github.com/dotnet/corefx/issues/33115)
  * [Wszystkie problemy z System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Problemy z System. Text. JSON oznaczone etykietą JSON-funkcja-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
