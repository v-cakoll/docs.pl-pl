---
title: -keycontainer (Opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970147"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (Opcje kompilatora C#)
Określa nazwę kontenera kluczy kryptograficznych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Argumenty  
 `string`  
 Nazwa kontenera kluczy silnej nazwy.  
  
## <a name="remarks"></a>Uwagi  
 Gdy używana jest opcja **-keycontainer,** kompilator tworzy składnik sharable. Kompilator wstawia klucz publiczny z określonego kontenera do manifestu zestawu i podpisuje końcowy zestaw kluczem prywatnym. Aby wygenerować plik `sn -k file` klucza, wpisz wiersz polecenia. `sn -i`instaluje parę kluczy w kontenerze. Ta opcja nie jest obsługiwana, gdy kompilator działa na coreclr. Aby podpisać zestaw podczas budowania na coreclr, należy użyć opcji [-keyfile.](keyfile-compiler-option.md)
  
 Jeśli skompilować z [-target:module](./target-module-compiler-option.md), nazwa pliku klucza jest utrzymywana w module i włączone do zestawu podczas kompilowania tego modułu do zestawu z [-addmodule](./addmodule-compiler-option.md).  
  
 Tę opcję można również określić jako<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>atrybut niestandardowy ( ) w kodzie źródłowym dla dowolnego modułu języka pośredniego firmy Microsoft (MSIL).  
  
 Można również przekazać informacje szyfrowania do kompilatora z [-keyfile](./keyfile-compiler-option.md). Użyj [-delaysign,](./delaysign-compiler-option.md) jeśli klucz publiczny ma zostać dodany do manifestu zestawu, ale chcesz opóźnić podpisanie zestawu, dopóki nie zostanie przetestowany.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../standard/assembly/create-use-strong-named.md) i [Opóźnianie podpisywania zestawu](../../../standard/assembly/delay-sign.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Ta opcja kompilatora nie jest dostępna w środowisku programistycznym programu Visual Studio.  
  
 Można programowo uzyskać dostęp do <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>tej opcji kompilatora z .  
  
## <a name="see-also"></a>Zobacz też

- [C# Kompilator -keyfile opcja](keyfile-compiler-option.md)
- [Opcje kompilatora Języka C#](index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
