---
title: Serializacja i deserializacja JSON C# przy użyciu-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: acb83be9b20a155b6b6a9fb5ade38e099f54e71d
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163595"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>Serializacja i deserializacja kodu JSON (kierowanie i cofanie) w programie .NET — Omówienie

Przestrzeń nazw `System.Text.Json` zawiera funkcje serializowania do i deserializacji z JavaScript Object Notation (JSON).

Projekt biblioteki wyróżnia wysoką wydajność i małą alokację pamięci w ramach rozbudowanego zestawu funkcji. Wbudowana obsługa UTF-8 optymalizuje proces odczytywania i pisania tekstu JSON zakodowanego w formacie UTF-8, który jest najbardziej rozpowszechnionym kodowaniem danych w sieci Web i plikach na dysku.

Biblioteka zawiera również klasy umożliwiające pracę z modelem DOM (Document objecting) w pamięci. Ta funkcja włącza losowy dostęp tylko do odczytu do elementów w pliku JSON lub ciągu. 

## <a name="how-to-get-the-library"></a>Jak uzyskać bibliotekę

* Biblioteka jest wbudowana w ramach platformy udostępnionej [.NET Core 3,0](https://aka.ms/netcore3download) .
* W przypadku innych platform docelowych Zainstaluj pakiet NuGet [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) . Pakiet obsługuje:
  * .NET Standard 2,0 i nowsze wersje
  * .NET Framework 4.7.2 i nowsze wersje
  * .NET Core 2,0, 2,1 i 2,2

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Jak używać biblioteki](system-text-json-how-to.md)
* [Jak przeprowadzić migrację z Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Jak pisać konwertery](system-text-json-converters-how-to.md)
* [System.Text.Json kod źródłowy](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [Dokumentacja interfejsu API System.Text.Json](xref:System.Text.Json)
* [System.Text.Json. Dokumentacja interfejsu API serializacji](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
