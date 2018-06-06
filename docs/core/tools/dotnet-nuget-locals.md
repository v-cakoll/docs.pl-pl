---
title: polecenie zmiennych lokalnych nuget DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie zmiennych lokalnych nuget dotnet czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 799acb92d6ab7439e15c23c9f0b7b572c966adda
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696874"
---
# <a name="dotnet-nuget-locals"></a>Zmienne lokalne nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget locals` — Usuwa lub wyświetla ich listę zasobów lokalnych NuGet.

## <a name="synopsis"></a>Streszczenie

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Opis

`dotnet nuget locals` Polecenie czyści lub wyświetla ich listę zasobów lokalnych NuGet w pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.

## <a name="arguments"></a>Argumenty

`CACHE_LOCATION`

Lokalizacja pamięci podręcznej listy lub wyczyścić. Przyjmuje jeden z następujących wartości:

* `all` — Wskazuje, że określona operacja jest stosowane do wszystkich typów pamięci podręcznej: pamięci podręcznej żądania http, pakiety globalnej pamięci podręcznej i tymczasowego pamięci podręcznej.
* `http-cache` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej żądania http. Nie ma wpływu na innych lokalizacji pamięci podręcznej.
* `global-packages` — Wskazuje, że określona operacja jest stosowane tylko do pakietów globalnej pamięci podręcznej. Nie ma wpływu na innych lokalizacji pamięci podręcznej.
* `temp` — Wskazuje, że określona operacja jest stosowane tylko do tymczasowego pamięci podręcznej. Nie ma wpływu na innych lokalizacji pamięci podręcznej.

## <a name="options"></a>Opcje

`--force-english-output`

Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-c|--clear`

Usuń zaznaczenie opcji wykonuje operację wyczyść na typ określony w pamięci podręcznej. Zawartość pamięci podręcznej katalogów jest rekursywnie usunięte. Wykonywanie użytkownika/grupy musi mieć uprawnienia do plików w katalogach pamięci podręcznej. W przeciwnym razie zostanie wyświetlony błąd wskazujący plików/folderów, które nie zostały wyczyszczone.

`-l|--list`

Opcja lista służy do wyświetlania lokalizacji pamięci podręcznej określonego typu.

## <a name="examples"></a>Przykłady

Wyświetla ścieżki wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http pakiety globalny katalog pamięci podręcznej i katalog tymczasowy pamięci podręcznej):

`dotnet nuget locals –l all`

Wyświetla ścieżkę dla katalogu lokalnej pamięci podręcznej http:

`dotnet nuget locals --list http-cache`

Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http pakiety globalny katalog pamięci podręcznej i katalog tymczasowy pamięci podręcznej):

`dotnet nuget locals --clear all`

Czyści wszystkie pliki w katalogu pamięci podręcznej lokalnego globalnego pakiety:

`dotnet nuget locals -c global-packages`

Czyści wszystkie pliki w lokalnej pamięci podręcznej tymczasowego katalogu:

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Aby uzyskać informacje dotyczące typowych problemów i błędów podczas korzystania z `dotnet nuget locals` polecenia, zobacz [Zarządzanie pamięci podręcznej NuGet](/nuget/consume-packages/managing-the-nuget-cache).