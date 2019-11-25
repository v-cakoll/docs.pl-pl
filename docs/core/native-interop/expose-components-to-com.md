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
ms.openlocfilehash: 8d9b8eb274777a0ed019a207c6e8610cc73ec390
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973313"
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

5. Dodaj atrybut `[Guid("<IID>")]` do interfejsu przy użyciu identyfikatora GUID interfejsu dla implementowanego interfejsu COM. Na przykład `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Należy zauważyć, że ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu dla modelu COM. W programie Visual Studio można wygenerować identyfikator GUID, przechodząc do menu Narzędzia > Utwórz GUID, aby otworzyć narzędzie Tworzenie identyfikatora GUID.
6. Dodaj atrybut `[InterfaceType]` do interfejsu i określ podstawowe interfejsy COM, które ma zaimplementować interfejs.
7. Utwórz klasę o nazwie `Server` implementującej `IServer`.
8. Dodaj atrybut `[Guid("<CLSID>")]` do klasy z identyfikatorem GUID klasy dla implementującej klasy COM. Na przykład `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Podobnie jak w przypadku identyfikatora GUID interfejsu, ten identyfikator GUID musi być unikatowy, ponieważ jest jedynym identyfikatorem tego interfejsu w modelu COM.
9. Dodaj atrybut `[ComVisible(true)]` do interfejsu i klasy.

> [!IMPORTANT]
> W przeciwieństwie do .NET Framework platforma .NET Core wymaga określenia identyfikatora CLSID każdej klasy, która ma być aktywowalnej za pośrednictwem modelu COM.

## <a name="generate-the-com-host"></a>Generowanie hosta COM

1. Otwórz plik projektu `.csproj` i Dodaj `<EnableComHosting>true</EnableComHosting>` wewnątrz tagu `<PropertyGroup></PropertyGroup>`.
2. Skompiluj projekt.

Wynikowe dane wyjściowe będą mieć `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` i `ProjectName.comhost.dll`.

## <a name="register-the-com-host-for-com"></a>Rejestrowanie hosta COM dla modelu COM

Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom `regsvr32 ProjectName.comhost.dll`. Spowoduje to zarejestrowanie wszystkich uwidocznionych obiektów .NET w modelu COM.

## <a name="enabling-regfree-com"></a>Włączanie nierejestrowanego COM

1. Otwórz plik projektu `.csproj` i Dodaj `<EnableRegFreeCom>true</EnableRegFreeCom>` wewnątrz tagu `<PropertyGroup></PropertyGroup>`.
2. Skompiluj projekt.

Wynikowe dane wyjściowe będą teraz również mieć plik `ProjectName.X.manifest`. Ten plik jest manifestem równoległym do użycia z modelem COM bez rejestru.

## <a name="sample"></a>Przykład

Istnieje w pełni funkcjonalny [przykład serwera com](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) w repozytorium dotnet/Samples w witrynie GitHub.

## <a name="additional-notes"></a>Dodatkowe uwagi

W przeciwieństwie do .NET Framework, nie ma obsługi w programie .NET Core do generowania biblioteki typów modelu COM (TLB) z zestawu .NET Core. Wskazówki dotyczą ręcznego zapisywania pliku IDL lub C/C++ nagłówka dla natywnych deklaracji interfejsów com.

Ponadto ładowanie obu .NET Framework i .NET Core do tego samego procesu ma ograniczenia diagnostyczne. Głównym ograniczeniem jest debugowanie składników zarządzanych, ponieważ nie jest możliwe debugowanie jednocześnie .NET Framework i .NET Core. Ponadto dwa wystąpienia środowiska uruchomieniowego nie współdzielą zestawów zarządzanych. Oznacza to, że nie jest możliwe udostępnianie rzeczywistych typów .NET między dwoma środowiskami uruchomieniowymi, a w zamian wszystkie interakcje muszą być ograniczone do umów dotyczących interfejsów COM.
