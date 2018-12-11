---
title: polecenie lokalne nuget DotNet
description: Polecenie lokalne nuget dotnet usuwa lub wyświetla ich listę zasobów lokalnych NuGet, takie jak pamięć podręczna żądań http, tymczasowej pamięci podręcznej lub folder komputera globalnymi pakietami.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: d0f1c7c2e0b233c214cc48d026c19755fc047bfa
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170759"
---
# <a name="dotnet-nuget-locals"></a>Zmienne lokalne nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget locals` -Usuwa lub wyświetla ich listę zasobów lokalnych NuGet.

## <a name="synopsis"></a>Streszczenie

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Opis

`dotnet nuget locals` Polecenie usuwa lub wyświetla ich listę zasobów lokalnych NuGet w pamięci podręcznej żądania http, tymczasowej pamięci podręcznej lub folder globalnymi pakietami dla komputera.

## <a name="arguments"></a>Argumenty

* **`CACHE_LOCATION`**

  Lokalizacja pamięci podręcznej, aby wyświetlić listę lub usuń zaznaczenie. Akceptuje ona jedną z następujących wartości:

  * `all` — Wskazuje, że określona operacja jest stosowana do wszystkich typów pamięci podręcznej: pamięć podręczna żądań http, pamięci podręcznej globalnymi pakietami i tymczasowej pamięci podręcznej.
  * `http-cache` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej żądania http. Nie ma wpływu na innych lokalizacji pamięci podręcznej.
  * `global-packages` — Wskazuje, że określona operacja jest stosowane tylko do pamięci podręcznej globalnymi pakietami. Nie ma wpływu na innych lokalizacji pamięci podręcznej.
  * `temp` — Wskazuje, że określona operacja jest stosowane tylko do tymczasowej pamięci podręcznej. Nie ma wpływu na innych lokalizacji pamięci podręcznej.

## <a name="options"></a>Opcje

* **`--force-english-output`**

  Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`-c|--clear`**

  Usuń zaznaczenie opcji wykonuje wyczyść operacji na typie określonym w pamięci podręcznej. Zawartość pamięci podręcznej katalogów są rekursywnie usunięte. Wykonywanie użytkownika/grupy musi mieć uprawnienia do plików w katalogach pamięci podręcznej. W przeciwnym razie zostanie wyświetlony błąd wskazujący plików/folderów, które nie zostały wyczyszczone.

* **`-l|--list`**

  Opcja listy jest używana do wyświetlania lokalizacji, typu określonego w pamięci podręcznej.

## <a name="examples"></a>Przykłady

* Wyświetla ścieżki wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http, katalog pamięci podręcznej globalnymi pakietami i katalog tymczasowy pamięci podręcznej):

  ```console
  dotnet nuget locals –l all
  ```

* Wyświetla ścieżkę do katalogu lokalnej pamięci podręcznej http:

  ```console
  dotnet nuget locals --list http-cache
  ```

* Czyści wszystkie pliki ze wszystkich katalogów lokalnej pamięci podręcznej (katalog pamięci podręcznej http, katalog pamięci podręcznej globalnymi pakietami i katalog tymczasowy pamięci podręcznej):

  ```console
  dotnet nuget locals --clear all
  ```

* Czyści wszystkie pliki w katalogu pamięci podręcznej lokalnej globalnymi pakietami:

  ```console
  dotnet nuget locals -c global-packages
  ```

* Czyści wszystkie pliki w katalogu lokalnym tymczasowa pamięć podręczna:

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Instrukcje dotyczące często występujących problemów i błędów podczas korzystania z `dotnet nuget locals` polecenia, zobacz [zarządzania pamięcią podręczną programu NuGet](/nuget/consume-packages/managing-the-nuget-cache).