---
title: polecenie locale dla pakietów NuGet dotnet
description: Polecenie locale polecenia NuGet programu dotnet czyści lub wyświetla listę lokalnych zasobów NuGet, takich jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503683"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet nuget locals` — czyści lub wyświetla lokalne zasoby NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget locals` czyści lub wyświetla listę lokalnych zasobów NuGet w pamięci podręcznej żądania HTTP, tymczasowej pamięci podręcznej lub na całej maszynie.

## <a name="arguments"></a>Argumenty

- **`CACHE_LOCATION`**

  Lokalizacja pamięci podręcznej do wyświetlenia lub wyczyszczenia. Akceptuje jedną z następujących wartości:

  * `all` — wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięć podręczna żądań HTTP, pamięć podręczna pakietów globalnych i tymczasowa pamięć podręczna.
  * `http-cache` — wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej żądania HTTP. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.
  * `global-packages` — wskazuje, że określona operacja jest stosowana tylko do globalnej pamięci podręcznej pakietów. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.
  * `temp` — wskazuje, że określona operacja jest stosowana tylko do tymczasowej pamięci podręcznej. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.

## <a name="options"></a>Opcje

- **`--force-english-output`**

  Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-c|--clear`**

  Opcja Clear wykonuje operację czyszczenia dla określonego typu pamięci podręcznej. Zawartość katalogów pamięci podręcznej jest usuwana rekursywnie. Wykonywany użytkownik/grupa musi mieć uprawnienia do plików w katalogach pamięci podręcznej. W przeciwnym razie zostanie wyświetlony komunikat o błędzie wskazujący pliki/foldery, które nie zostały wyczyszczone.

- **`-l|--list`**

  Opcja Lista służy do wyświetlania lokalizacji określonego typu pamięci podręcznej.

## <a name="examples"></a>Przykłady

- Wyświetla ścieżki wszystkich lokalnych katalogów pamięci podręcznej (Katalog pamięci podręcznej http, Katalog pamięci podręcznej pakietów globalnych i tymczasowy katalog pamięci podręcznej):

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- Wyświetla ścieżkę dla lokalnego katalogu pamięci podręcznej http:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- Czyści wszystkie pliki z katalogów lokalnej pamięci podręcznej (Katalog pamięci podręcznej http, Katalog pamięci podręcznej pakietów globalnych i tymczasowy katalog pamięci podręcznej):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- Czyści wszystkie pliki w lokalnym katalogu globalnym pakietów pamięci podręcznej:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- Czyści wszystkie pliki w lokalnym katalogu tymczasowej pamięci podręcznej:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Informacje o typowych problemach i błędach przy użyciu polecenia `dotnet nuget locals` można znaleźć w temacie [Zarządzanie pamięcią podręczną NuGet](/nuget/consume-packages/managing-the-nuget-cache).
