---
title: dotnet nuget locals polecenie
description: Polecenie dotnet nuget locals czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań http, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503683"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet nuget locals`- Czyści lub wyświetla lokalne zasoby NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget locals` czyści lub wyświetla lokalne zasoby NuGet w pamięci podręcznej żądań http, tymczasowej pamięci podręcznej lub folderze pakietów globalnych dla całego komputera.

## <a name="arguments"></a>Argumenty

- **`CACHE_LOCATION`**

  Lokalizacja pamięci podręcznej do listy lub wyczyścić. Akceptuje jedną z następujących wartości:

  * `all`- Wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięci podręcznej żądań http, pamięci podręcznej pakietów globalnych i tymczasowej pamięci podręcznej.
  * `http-cache`- Wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej żądań http. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.
  * `global-packages`- Wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej pakietów globalnych. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.
  * `temp`- Wskazuje, że określona operacja jest stosowana tylko do tymczasowej pamięci podręcznej. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.

## <a name="options"></a>Opcje

- **`--force-english-output`**

  Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-c|--clear`**

  Opcja wyczyść wykonuje wyczyść operację na określonym typie pamięci podręcznej. Zawartość katalogów pamięci podręcznej są usuwane cyklicznie. Wykonujący użytkownik/grupa musi mieć uprawnienia do plików w katalogach pamięci podręcznej. Jeśli nie, zostanie wyświetlony błąd wskazujący pliki/foldery, które nie zostały wyczyszczone.

- **`-l|--list`**

  Opcja listy służy do wyświetlania lokalizacji określonego typu pamięci podręcznej.

## <a name="examples"></a>Przykłady

- Wyświetla ścieżki wszystkich lokalnych katalogów pamięci podręcznej (katalog pamięci podręcznej http-cache, katalog pamięci podręcznej pakietów globalnych i katalog pamięci podręcznej tymczasowej):

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- Wyświetla ścieżkę dla lokalnego katalogu http-cache:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http-cache, katalog pamięci podręcznej pakietów globalnych i katalog pamięci podręcznej tymczasowej):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- Czyści wszystkie pliki w katalogu pamięci podręcznej lokalnych pakietów globalnych:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- Czyści wszystkie pliki w lokalnym katalogu tymczasowej pamięci podręcznej:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Aby uzyskać informacje na temat `dotnet nuget locals` typowych problemów i błędów podczas korzystania z polecenia, zobacz [Zarządzanie pamięcią podręczną NuGet](/nuget/consume-packages/managing-the-nuget-cache).
