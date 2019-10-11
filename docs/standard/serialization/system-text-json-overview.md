---
title: Serializacja i deserializacja JSON C# przy użyciu-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 5ce98a7908470a402779436db43333d46f5101fc
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180154"
---
# <a name="json-serialization-in-net---overview"></a>Serializacja kodu JSON w programie .NET — Omówienie

Przestrzeń nazw `System.Text.Json` zawiera funkcje serializowania do i deserializacji z JavaScript Object Notation (JSON).

Projekt biblioteki wyróżnia wysoką wydajność i małą alokację pamięci w ramach rozbudowanego zestawu funkcji. Wbudowana obsługa UTF-8 optymalizuje proces odczytywania i pisania tekstu JSON zakodowanego w formacie UTF-8, który jest najbardziej rozpowszechnionym kodowaniem danych w sieci Web i plikach na dysku.

Biblioteka zawiera również klasy umożliwiające pracę z modelem DOM (Document objecting) w pamięci. Ta funkcja włącza losowy dostęp tylko do odczytu do elementów w pliku JSON lub ciągu. 

## <a name="how-to-get-the-library"></a>Jak uzyskać bibliotekę

* Biblioteka jest wbudowana w ramach platformy udostępnionej [.NET Core 3,0](https://aka.ms/netcore3download) .
* W przypadku innych platform docelowych Zainstaluj pakiet NuGet [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) . Pakiet obsługuje:
  * .NET Standard 2,0 i nowsze wersje
  * .NET Framework 4.6.1 i nowsze wersje
  * .NET Core 2,0, 2,1 i 2,2

## <a name="additional-resources"></a>Zasoby dodatkowe

* [Jak używać biblioteki](system-text-json-how-to.md)
* [Kod źródłowy](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [Dokumentacja interfejsu API](xref:System.Text.Json)
* [Harmonogram działania](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* Problemy z usługą GitHub w repozytorium dotnet/corefx
  * [Omówienie tworzenia pliku System. Text. JSON](https://github.com/dotnet/corefx/issues/33115)
  * [Wszystkie problemy z System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Problemy z System. Text. JSON oznaczone etykietą JSON-funkcja-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
