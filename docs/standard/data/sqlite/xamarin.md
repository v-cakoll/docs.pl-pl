---
title: Ograniczenia dotyczące platformy Xamarin
ms.date: 12/13/2019
description: W tym artykule opisano niektóre ograniczenia, które można napotkać podczas korzystania z platformy Xamarin.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447168"
---
# <a name="xamarin-limitations"></a>Ograniczenia dotyczące platformy Xamarin

Elementy docelowe Microsoft. Data. sqlite .NET Standard 2,0 i są obsługiwane w środowisku Xamarin. W poniższej tabeli przedstawiono, które platformy domyślny pakiet SQLitePCLRaw zapewnia natywne pliki binarne oprogramowania SQLite dla programu. Zobacz [niestandardowe wersje oprogramowania SQLite](custom-versions.md) , aby uzyskać szczegółowe informacje na temat korzystania z innego pakietu lub udostępniania natywnych plików binarnych oprogramowania SQLite.

| Platforma | Pliki binarne oprogramowania SQLite |
| --- | --- |
| **Xamarin.Android** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | ✔ |
| **Xamarin.iOS** | ✔ |
| **Xamarin.Mac** | ✔ |
| **Xamarin. systemu TVOS** | ✔ |
| **PLATFORMY UNIWERSALNEJ SYSTEMU WINDOWS** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |

## <a name="ios"></a>iOS

Firma Microsoft. Data. sqlite próbuje automatycznie zainicjować zbiory SQLitePCLRaw. Niestety, ze względu na ograniczenia w kompilacji z wyprzedzeniem (AOT) dla platformy Xamarin. iOS, próba nie powiedzie się i zostanie wyświetlony następujący błąd.

> Musisz wywołać `SQLitePCL.raw.SetProvider()`. Jeśli korzystasz z pakietu pakietów, możesz to zrobić, wywołując `SQLitePCL.Batteries.Init()`.

Aby zainicjować pakiet, Dodaj następujący wiersz kodu do aplikacji przed użyciem Microsoft. Data. sqlite.

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a>Zobacz także

* [Ograniczenia asynchroniczne](async.md)
* [Niestandardowe wersje programu SQLite](custom-versions.md)
