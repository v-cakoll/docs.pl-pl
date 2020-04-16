---
title: dotnet nuget locals polecenia
description: Polecenie dotnet nuget locals czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań http, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całej maszyny.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 5b421b5058528a93c7be58eef2932937cc9cc12d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463535"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget locals`- Czyści lub wyświetla lokalne zasoby NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]

dotnet nuget locals -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget locals` czyści lub wyświetla lokalne zasoby NuGet w pamięci podręcznej żądań http, tymczasowej pamięci podręcznej lub folderze pakietów globalnych dla całej maszyny.

## <a name="arguments"></a>Argumenty

- **`CACHE_LOCATION`**

  Lokalizacja pamięci podręcznej do wyświetlenia lub wyczyszczenie. Akceptuje jedną z następujących wartości:

  * `all`- Wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięci podręcznej żądania http, pamięci podręcznej pakietów globalnych i tymczasowej pamięci podręcznej.
  * `http-cache`- Wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej żądań http. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.
  * `global-packages`- Wskazuje, że określona operacja jest stosowana tylko do globalnej pamięci podręcznej pakietów. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.
  * `temp`- Wskazuje, że określona operacja jest stosowana tylko do tymczasowej pamięci podręcznej. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.

## <a name="options"></a>Opcje

- **`--force-english-output`**

  Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-c|--clear`**

  Opcja clear wykonuje wyczyść operację na określony typ pamięci podręcznej. Zawartość katalogów pamięci podręcznej są usuwane cyklicznie. Wykonujący użytkownik/grupa musi mieć uprawnienia do plików w katalogach pamięci podręcznej. Jeśli nie, zostanie wyświetlony błąd wskazujący pliki/foldery, które nie zostały wyczyszczone.

- **`-l|--list`**

  Opcja listy służy do wyświetlania lokalizacji określonego typu pamięci podręcznej.

## <a name="examples"></a>Przykłady

- Wyświetla ścieżki wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http, katalog pamięci podręcznej pakietów globalnych i katalog pamięci podręcznej tymczasowej pamięci podręcznej):

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- Wyświetla ścieżkę dla lokalnego katalogu http-cache:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog http-cache, katalog pamięci podręcznej pakietów globalnych i katalog pamięci podręcznej tymczasowej):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- Czyści wszystkie pliki w katalogu lokalnej pamięci podręcznej pakietów globalnych:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- Czyści wszystkie pliki w lokalnym katalogu tymczasowej pamięci podręcznej:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Aby uzyskać informacje na temat typowych problemów i błędów podczas korzystania z `dotnet nuget locals` polecenia, zobacz Zarządzanie [pamięcią podręczną NuGet](/nuget/consume-packages/managing-the-nuget-cache).
