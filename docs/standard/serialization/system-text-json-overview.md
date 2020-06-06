---
title: Serializowanie i deserializacja JSON przy użyciu języka C# — .NET
description: To omówienie zawiera opis System.Text.Json funkcji przestrzeni nazw do serializacji do i deserializacji z JSON w programie .NET.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 909d979d46b30939e304af071de65d230febd92d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "83380125"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>Serializacja i deserializacja kodu JSON (kierowanie i cofanie) w programie .NET — Omówienie

`System.Text.Json`Przestrzeń nazw zawiera funkcje serializacji do i deserializacji z JavaScript Object Notation (JSON).

Projekt biblioteki wyróżnia wysoką wydajność i małą alokację pamięci w ramach rozbudowanego zestawu funkcji. Wbudowana obsługa UTF-8 optymalizuje proces odczytywania i pisania tekstu JSON zakodowanego w formacie UTF-8, który jest najbardziej rozpowszechnionym kodowaniem danych w sieci Web i plikach na dysku.

Biblioteka zawiera również klasy umożliwiające pracę z modelem DOM (Document objecting) w pamięci. Ta funkcja włącza losowy dostęp tylko do odczytu do elementów w pliku JSON lub ciągu.

## <a name="how-to-get-the-library"></a>Jak uzyskać bibliotekę

* Biblioteka jest wbudowana w ramach platformy udostępnionej [.NET Core 3,0](https://aka.ms/netcore3download) .
* W przypadku innych platform docelowych zainstaluj [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) pakiet NuGet. Pakiet obsługuje:
  * .NET Standard 2,0 i nowsze wersje
  * .NET Framework 4.7.2 i nowsze wersje
  * .NET Core 2,0, 2,1 i 2,2

## <a name="additional-resources"></a>Zasoby dodatkowe

* [Jak używać biblioteki](system-text-json-how-to.md)
* [Jak przeprowadzić migrację zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Jak pisać konwertery](system-text-json-converters-how-to.md)
* [System.Text.Jsonkod źródłowy](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [System.Text.JsonDokumentacja interfejsu API](xref:System.Text.Json)
* [System.Text.Json. Dokumentacja interfejsu API serializacji](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
