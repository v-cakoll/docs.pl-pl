---
title: Wystawianie składników .NET Core do com
description: W tym samouczku pokazano, jak udostępnić klasę do com z .NET Core. Serwer COM i manifest serwera side-by-side dla com bez rejestru.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 98d303c99693a8aadb23da509a700772db69c0e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146661"
---
# <a name="exposing-net-core-components-to-com"></a>Wystawianie składników .NET Core do com

W .NET Core proces ujawniania obiektów .NET do com został znacznie usprawniony w porównaniu do .NET Framework. Poniższy proces przeprowadzi Cię przez jak udostępnić klasy do COM. Ten samouczek przedstawia sposób wykonania następujących czynności:

- Uwidaczniaklasę do com z .NET Core.
- Wygeneruj serwer COM w ramach tworzenia biblioteki .NET Core.
- Automatycznie generuj manifest serwera side-by-side dla com bez rejestru.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj [zestaw SDK .NET Core 3.0](https://dotnet.microsoft.com/download) lub nowszą wersję.

## <a name="create-the-library"></a>Tworzenie biblioteki

Pierwszym krokiem jest utworzenie biblioteki.

1. Utwórz nowy folder, a w tym folderze uruchom następujące polecenie:

    ```dotnetcli
    dotnet new classlib
    ```

2. Otwórz plik `Class1.cs`.
3. Dodaj `using System.Runtime.InteropServices;` do górnej części pliku.
4. Utwórz interfejs `IServer`o nazwie . Przykład:

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. Dodaj `[Guid("<IID>")]` atrybut do interfejsu, z interfejsem GUID dla interfejsu COM, który implementujesz. Na przykład `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Należy zauważyć, że ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu dla modelu COM. W programie Visual Studio można wygenerować identyfikator GUID, przechodząc do narzędzia > tworzenie identyfikatora GUID, aby otworzyć narzędzie Tworzenie identyfikatora GUID.
6. Dodaj `[InterfaceType]` atrybut do interfejsu i określ, jakie podstawowe interfejsy COM powinien zaimplementować interfejs.
7. Utwórz klasę `Server` o `IServer`nazwie, która implementuje .
8. Dodaj `[Guid("<CLSID>")]` atrybut do klasy, z identyfikatorem identyfikatora klasy GUID dla klasy COM, którą implementujesz. Na przykład `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Podobnie jak w interfejsie GUID, ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu do modelu COM.
9. Dodaj `[ComVisible(true)]` atrybut do interfejsu i klasy.

> [!IMPORTANT]
> W przeciwieństwie do programu .NET Framework program .NET Core wymaga określenia identyfikatora CLSID dowolnej klasy, którą chcesz aktywować za pośrednictwem systemu COM.

## <a name="generate-the-com-host"></a>Generowanie hosta COM

1. Otwórz `.csproj` plik projektu `<EnableComHosting>true</EnableComHosting>` i `<PropertyGroup></PropertyGroup>` dodaj wewnątrz znacznika.
2. Skompiluj projekt.

Wynikowe dane wyjściowe `ProjectName.dll` `ProjectName.deps.json`będą `ProjectName.runtimeconfig.json` `ProjectName.comhost.dll` miały , i plik.

## <a name="register-the-com-host-for-com"></a>Zarejestruj hosta COM dla COM

Otwórz wiersz polecenia z `regsvr32 ProjectName.comhost.dll`podwyższonym poziomem uprawnień i uruchom . Spowoduje to zarejestrowanie wszystkich narażonych obiektów .NET w kom.

## <a name="enabling-regfree-com"></a>Włączanie regfree COM

1. Otwórz `.csproj` plik projektu `<EnableRegFreeCom>true</EnableRegFreeCom>` i `<PropertyGroup></PropertyGroup>` dodaj wewnątrz znacznika.
2. Skompiluj projekt.

Wynikowe dane wyjściowe będą `ProjectName.X.manifest` teraz również mieć plik. Ten plik jest manifestem side-by-side do użytku z com bez rejestru.

## <a name="sample"></a>Sample

W [repozytorium](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) dotnet/samples w githubie znajduje się w pełni funkcjonalny przykład serwera COM.

## <a name="additional-notes"></a>Uwagi dodatkowe

W przeciwieństwie do programu .NET Framework w platformie .NET Core nie ma obsługi generowania biblioteki typów COM (TLB) z zestawu .NET Core. Wskazówki dotyczące ręcznego zapisu pliku IDL lub nagłówka C/C++ dla natywnych deklaracji interfejsów COM.

Ponadto ładowanie zarówno .NET Framework i .NET Core do tego samego procesu ma ograniczenia diagnostyczne. Podstawowym ograniczeniem jest debugowanie zarządzanych składników, ponieważ nie jest możliwe debugowanie zarówno .NET Framework, jak i .NET Core w tym samym czasie. Ponadto dwa wystąpienia czasu uruchomieniowego nie współużytkują zestawów zarządzanych. Oznacza to, że nie jest możliwe udostępnianie rzeczywistych typów platformy .NET w dwóch wykonawczych i zamiast tego wszystkie interakcje muszą być ograniczone do kontraktów interfejsu uniewinnionego com.
