---
title: polecenie locale dla pakietów NuGet dotnet
description: Polecenie locale polecenia NuGet programu dotnet czyści lub wyświetla listę lokalnych zasobów NuGet, takich jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 482e841d3b402084eb8c7f2456779f1600a5dd19
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117626"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Ten temat dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget locals`-Czyści lub wyświetla lokalne zasoby NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Opis

`dotnet nuget locals` Polecenie czyści lub wyświetla listę lokalnych zasobów NuGet w folderze pamięci podręcznej żądania HTTP, tymczasowej pamięci podręcznej lub na całej maszynie.

## <a name="arguments"></a>Argumenty

* **`CACHE_LOCATION`**

  Lokalizacja pamięci podręcznej do wyświetlenia lub wyczyszczenia. Akceptuje jedną z następujących wartości:

  * `all`-Wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięć podręczna żądań HTTP, pamięć podręczna pakietów globalnych i tymczasowa pamięć podręczna.
  * `http-cache`-Wskazuje, że określona operacja jest stosowana tylko do pamięci podręcznej żądania HTTP. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.
  * `global-packages`-Wskazuje, że określona operacja jest stosowana tylko do globalnej pamięci podręcznej pakietów. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.
  * `temp`-Wskazuje, że określona operacja jest stosowana tylko do tymczasowej pamięci podręcznej. Nie ma to wpływu na inne lokalizacje pamięci podręcznej.

## <a name="options"></a>Opcje

* **`--force-english-output`**

  Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`-c|--clear`**

  Opcja Clear wykonuje operację czyszczenia dla określonego typu pamięci podręcznej. Zawartość katalogów pamięci podręcznej jest usuwana rekursywnie. Wykonywany użytkownik/grupa musi mieć uprawnienia do plików w katalogach pamięci podręcznej. W przeciwnym razie zostanie wyświetlony komunikat o błędzie wskazujący pliki/foldery, które nie zostały wyczyszczone.

* **`-l|--list`**

  Opcja Lista służy do wyświetlania lokalizacji określonego typu pamięci podręcznej.

## <a name="examples"></a>Przykłady

* Wyświetla ścieżki wszystkich lokalnych katalogów pamięci podręcznej (Katalog pamięci podręcznej http, Katalog pamięci podręcznej pakietów globalnych i tymczasowy katalog pamięci podręcznej):

  ```dotnetcli
  dotnet nuget locals –l all
  ```

* Wyświetla ścieżkę dla lokalnego katalogu pamięci podręcznej http:

  ```dotnetcli
  dotnet nuget locals --list http-cache
  ```

* Czyści wszystkie pliki z katalogów lokalnej pamięci podręcznej (Katalog pamięci podręcznej http, Katalog pamięci podręcznej pakietów globalnych i tymczasowy katalog pamięci podręcznej):

  ```dotnetcli
  dotnet nuget locals --clear all
  ```

* Czyści wszystkie pliki w lokalnym katalogu globalnym pakietów pamięci podręcznej:

  ```dotnetcli
  dotnet nuget locals -c global-packages
  ```

* Czyści wszystkie pliki w lokalnym katalogu tymczasowej pamięci podręcznej:

  ```dotnetcli
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Informacje o typowych problemach i błędach przy użyciu `dotnet nuget locals` polecenia znajdują się w temacie [Zarządzanie pamięcią podręczną NuGet](/nuget/consume-packages/managing-the-nuget-cache).
