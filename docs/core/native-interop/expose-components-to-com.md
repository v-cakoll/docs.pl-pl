---
title: Udostępnianie składników .NET Core w ucho.
description: W tym samouczku pokazano, jak udostępnić klasę com z platformy .NET Core. Wygenerujesz serwer COM i manifest serwera side-by-side dla com bez rejestru.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 17d85b9e9734fae0bb69f94da8c08669216ab0ae
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242871"
---
# <a name="exposing-net-core-components-to-com"></a>Udostępnianie składników .NET Core w ucho.

W .NET Core proces wystawiania obiektów platformy .NET na urządzenie .NET został znacznie usprawniony w porównaniu z programem .NET Framework. Poniższy proces poprowadzi Cię przez jak udostępnić klasę do COM. Ten samouczek przedstawia sposób wykonania następujących czynności:

- Uwidacznianie klasy do com z .NET Core.
- Generowanie serwera COM w ramach tworzenia biblioteki .NET Core.
- Automatycznie wygeneruj manifest serwera obok siebie dla com bez rejestru.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj [pakiet .NET Core 3.0 SDK](https://dotnet.microsoft.com/download) lub nowszą wersję.

## <a name="create-the-library"></a>Tworzenie biblioteki

Pierwszym krokiem jest utworzenie biblioteki.

1. Utwórz nowy folder, a w tym folderze uruchom następujące polecenie:

    ```dotnetcli
    dotnet new classlib
    ```

2. Otwórz plik `Class1.cs`.
3. Dodaj `using System.Runtime.InteropServices;` do górnej części pliku.
4. Tworzenie interfejsu `IServer`o nazwie . Przykład:

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

5. Dodaj `[Guid("<IID>")]` atrybut do interfejsu z identyfikatorem GUID interfejsu interfejsu com, który implementujesz. Na przykład `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Należy zauważyć, że ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu dla com. W programie Visual Studio można wygenerować identyfikator GUID, przechodząc do narzędzia > tworzenie identyfikatora GUID, aby otworzyć narzędzie Tworzenie identyfikatora GUID.
6. Dodaj `[InterfaceType]` atrybut do interfejsu i określ, jakie podstawowe interfejsy COM interfejs powinien zaimplementować.
7. Utwórz klasę `Server` o `IServer`nazwie, która implementuje .
8. Dodaj `[Guid("<CLSID>")]` atrybut do klasy z identyfikatorem klasy guiD dla klasy COM, którą implementujesz. Na przykład `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Podobnie jak w interfejsie GUID interfejsu, ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu do com.
9. Dodaj `[ComVisible(true)]` atrybut do interfejsu i klasy.

> [!IMPORTANT]
> W przeciwieństwie do programu .NET Framework program .NET Core wymaga określenia clsid dowolnej klasy, którą chcesz aktywować za pośrednictwem programu COM.

## <a name="generate-the-com-host"></a>Generowanie hosta COM

1. Otwórz `.csproj` plik projektu `<EnableComHosting>true</EnableComHosting>` i `<PropertyGroup></PropertyGroup>` dodaj go wewnątrz znacznika.
2. Skompiluj projekt.

Wynikowy wynik będzie `ProjectName.dll`miał `ProjectName.deps.json` `ProjectName.runtimeconfig.json` plik `ProjectName.comhost.dll` , i plik.

## <a name="register-the-com-host-for-com"></a>Zarejestruj hosta COM dla com

Otwórz wiersz polecenia z `regsvr32 ProjectName.comhost.dll`podwyższonym poziomem uprawnień i uruchom polecenie . Spowoduje to zarejestrowanie wszystkich obiektów platformy .NET w aplikacji COM.

## <a name="enabling-regfree-com"></a>Włączanie regfree COM

1. Otwórz `.csproj` plik projektu `<EnableRegFreeCom>true</EnableRegFreeCom>` i `<PropertyGroup></PropertyGroup>` dodaj go wewnątrz znacznika.
2. Skompiluj projekt.

Wynikowe dane wyjściowe będą `ProjectName.X.manifest` teraz również mieć plik. Ten plik jest manifestem side-by-side do użytku z com bez rejestru.

## <a name="sample"></a>Przykład

Istnieje w pełni funkcjonalny [przykład serwera COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) w repozytorium dotnet/samples w usłudze GitHub.

## <a name="additional-notes"></a>Uwagi dodatkowe

W przeciwieństwie do programu .NET Framework w systemie .NET Core nie ma obsługi generowania biblioteki typów COM (TLB) z zestawu .NET Core. Wskazówki są albo ręcznie napisać plik IDL lub nagłówek C/C++ dla natywnych deklaracji interfejsów COM.

[Samodzielne wdrożenia](../deploying/index.md#publish-self-contained) składników COM nie są obsługiwane. Obsługiwane są tylko [wdrożenia zależne od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) składników COM.

Ponadto ładowanie programu .NET Framework i .NET Core do tego samego procesu ma ograniczenia diagnostyczne. Podstawowym ograniczeniem jest debugowanie składników zarządzanych, ponieważ nie jest możliwe debugowanie zarówno platformy .NET Framework, jak i .NET Core w tym samym czasie. Ponadto dwa wystąpienia środowiska uruchomieniowego nie współużytkują zestawy zarządzane. Oznacza to, że nie jest możliwe udostępnianie rzeczywistych typów .NET w dwóch środowiskach wykonywania, a zamiast tego wszystkie interakcje muszą być ograniczone do umów interfejsu COM narażonych.
