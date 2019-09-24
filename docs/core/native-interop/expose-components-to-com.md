---
title: Udostępnianie składników .NET Core do modelu COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 8f9624414a2b423bd43e8790d11b70ae1ca6286d
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216225"
---
# <a name="exposing-net-core-components-to-com"></a>Udostępnianie składników .NET Core do modelu COM

W programie .NET Core proces uwidaczniania obiektów .NET do modelu COM został znacznie ulepszony w porównaniu do .NET Framework. Poniższy proces przeprowadzi Cię przez sposób udostępnienia klasy modelowi COM. W tym samouczku pokazano, jak:

- Uwidocznij klasę modelu COM z platformy .NET Core.
- Wygeneruj serwer COM w ramach tworzenia biblioteki .NET Core.
- Automatycznie Generuj manifest serwera Side-by-Side dla modelu COM bez rejestracji.

## <a name="prerequisites"></a>Wymagania wstępne

- Zainstaluj program [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download) lub nowszą wersję.

## <a name="create-the-library"></a>Utwórz bibliotekę

Pierwszym krokiem jest utworzenie biblioteki.

1. Utwórz nowy folder, a w tym folderze Uruchom następujące polecenie:
    
    ```dotnetcli
    dotnet new classlib
    ```

2. Otwórz `Class1.cs`.
3. Dodaj `using System.Runtime.InteropServices;` na początku pliku.
4. Utwórz interfejs o nazwie `IServer`. Na przykład:

   [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]

5. `[Guid("<IID>")]` Dodaj atrybut do interfejsu przy użyciu identyfikatora GUID interfejsu dla implementowanego interfejsu com. Na przykład `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Należy zauważyć, że ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu dla modelu COM. W programie Visual Studio można wygenerować identyfikator GUID, przechodząc do menu Narzędzia > Utwórz GUID, aby otworzyć narzędzie Tworzenie identyfikatora GUID.
6. `[InterfaceType]` Dodaj atrybut do interfejsu i określ podstawowe interfejsy com, które ma zaimplementować interfejs.
7. Utwórz klasę o nazwie `Server` implementującej `IServer`.
8. `[Guid("<CLSID>")]` Dodaj atrybut do klasy przy użyciu identyfikatora klasy GUID dla implementującej klasy com. Na przykład `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Podobnie jak w przypadku identyfikatora GUID interfejsu, ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu w modelu COM.
9. `[ComVisible(true)]` Dodaj atrybut do interfejsu i klasy.

> [!IMPORTANT]
> W przeciwieństwie do .NET Framework platforma .NET Core wymaga określenia identyfikatora CLSID każdej klasy, która ma być aktywowalnej za pośrednictwem modelu COM.

## <a name="generate-the-com-host"></a>Generowanie hosta COM

1. Otwórz plik `<EnableComHosting>true</EnableComHosting>` projektu i Dodaj wewnątrz `<PropertyGroup></PropertyGroup>` znacznika. `.csproj`
2. Skompiluj projekt.

Wynikowe dane wyjściowe będą mieć `ProjectName.dll`plik `ProjectName.deps.json` `ProjectName.runtimeconfig.json` , i `ProjectName.comhost.dll` .

## <a name="register-the-com-host-for-com"></a>Rejestrowanie hosta COM dla modelu COM

Otwórz wiersz polecenia z podwyższonym poziomem `regsvr32 ProjectName.comhost.dll`uprawnień i uruchom polecenie. Spowoduje to zarejestrowanie wszystkich uwidocznionych obiektów .NET w modelu COM.

## <a name="enabling-regfree-com"></a>Włączanie nierejestrowanego COM

1. Otwórz plik `<EnableRegFreeCom>true</EnableRegFreeCom>` projektu i Dodaj wewnątrz `<PropertyGroup></PropertyGroup>` znacznika. `.csproj`
2. Skompiluj projekt.

Wynikowe dane wyjściowe będą teraz również mieć `ProjectName.X.manifest` plik. Ten plik jest manifestem równoległym do użycia z modelem COM bez rejestru.

## <a name="sample"></a>Przykład

Istnieje w pełni funkcjonalny [przykład serwera com](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) w repozytorium dotnet/Samples w witrynie GitHub.

## <a name="additional-notes"></a>Dodatkowe uwagi

W przeciwieństwie do .NET Framework, nie ma obsługi w programie .NET Core do generowania biblioteki typów modelu COM (TLB) z zestawu .NET Core. Trzeba będzie ręcznie napisać plik IDL lub C++ nagłówek dla natywnych deklaracji interfejsów.

Ponadto ładowanie zarówno .NET Framework, jak i .NET Core do tego samego procesu nie jest obsługiwane i w wyniku załadowania serwera .NET Core COM do procesu klienta .NET Framework COM lub odwrotnie nie jest obsługiwane.
