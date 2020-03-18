---
title: -platform (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5150e871d75c3c34dab10f10cdac3d8322d7a834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70849869"
---
# <a name="-platform-c-compiler-options"></a>-platform (Opcje kompilatora C#)

Określa, która wersja common language runtime (CLR) może uruchomić zestaw.

## <a name="syntax"></a>Składnia

```console
-platform:string
```

## <a name="parameters"></a>Parametry

`string` \
anycpu (domyślnie), anycpu32bitpreferred, ARM, x64, x86 lub Itanium.

## <a name="remarks"></a>Uwagi

- **anycpu** (domyślnie) kompiluje zestawu do uruchomienia na dowolnej platformie. Aplikacja jest uruchamiana jako proces 64-bitowy, gdy jest to możliwe i powraca do 32-bitowych, gdy tylko ten tryb jest dostępny.

- **anycpu32bitpreferred** kompiluje swój zestaw do uruchamiania na dowolnej platformie. Aplikacja działa w trybie 32-bitowym w systemach obsługujących zarówno aplikacje 64-bitowe, jak i 32-bitowe. Tę opcję można określić tylko dla projektów, które są przeznaczone dla .NET Framework 4.5.

- **ARM** kompiluje zestaw do uruchamiania na komputerze z procesorem ARM (Advanced RISC Machine).

- **ARM64** kompiluje zestaw do uruchamiania przez 64-bitowy clr na komputerze z procesorem Advanced RISC Machine (ARM), który obsługuje zestaw instrukcji A64.

- **x64** kompiluje swój zestaw do uruchomienia przez 64-bitowy clr na komputerze obsługującym zestaw instrukcji AMD64 lub EM64T.

- **x86** kompiluje swój zestaw do uruchomienia przez 32-bitowy, zgodny z x86 CLR.

- **Itanium** kompiluje swój zestaw do uruchomienia przez 64-bitowy CLR na komputerze z procesorem Itanium.

W 64-bitowym systemie operacyjnym Windows:

- Zestawy skompilowane z **-platform:x86** wykonać na 32-bitowej clr działa w ramach WOW64.

- DLL skompilowany z **-platform:anycpu** wykonuje na tym samym CLR jako proces, do którego jest ładowany.

- Pliki wykonywalne, które są kompilowane z **-platform:anycpu** wykonać na 64-bitowy CLR.

- Pliki wykonywalne skompilowane z **-platform:anycpu32bitpreferred** wykonać na 32-bitowym CLR.

Ustawienie **anycpu32bitpreferred** jest ważne tylko dla pliku wykonywalnego (. EXE) i wymaga .NET Framework 4.5.

Aby uzyskać więcej informacji na temat tworzenia aplikacji do uruchamiania w systemie operacyjnym Windows 64-bitowy, zobacz [Aplikacje 64-bitowe](../../../framework/64-bit-apps.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz stronę **Właściwości** projektu.

2. Kliknij stronę **Właściwości kompilacji.**

3. Zmodyfikuj **właściwość docelową platformy** i w przypadku projektów docelowych programu .NET Framework 4.5 zaznacz lub wyczyść pole wyboru **Preferuj 32-bitowe.**

> [!NOTE]
> `-platform`nie jest dostępna w środowisku programistycznym w programie Visual C# Express.

Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>kompilatora, zobacz .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak użyć opcji **-platform,** aby określić, że aplikacja powinna być uruchamiana przez 64-bitowy clr w 64-bitowym systemie operacyjnym Windows.

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
