---
title: -keycontainer (opcje kompilatora C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 57d3acb4fe128e07020bfe7c85ed86563b16f40a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467548"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (opcje kompilatora C#)
Określa nazwę kontenera kluczy kryptograficznych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Argumenty  
 `string`  
 Nazwa kontenera klucza silnej nazwy.  
  
## <a name="remarks"></a>Uwagi  
 Gdy **- keycontainer** jest używana opcja, kompilator tworzy składnik, które można udostępnić. Kompilator wstawia klucz publiczny z określonego kontenera do manifestu zestawu i podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia. `sn -i` Instaluje parę kluczy w kontenerze. Ta opcja nie jest obsługiwana, gdy kompilator jest uruchamiany w środowisku CoreCLR. Aby podpisać zestaw, podczas tworzenia w środowisku CoreCLR, należy użyć [- keyfile](keyfile-compiler-option.md) opcji.
  
 Jeśli kompilujesz z opcją [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), nazwę pliku klucza jest przechowywany w module i dołączone do zestawu podczas kompilowania tego modułu do zestawu z [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Można również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) w kodzie źródłowym dla każdego modułu języka intermediate language (MSIL) firmy Microsoft.  
  
 Można również przekazać szyfrowania informacji do kompilatora przy użyciu [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Użyj [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli chcesz, aby klucz publiczny, dodać do manifestu zestawu, ale opóźnić podpisywanie zestawu, dopóki nie został przetestowany.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnienie podpisywania zestawu](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Ta opcja kompilatora nie jest dostępna w środowisku programowania Visual Studio.  
  
 Programowego dostępu do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Zobacz też

- [-Keyfile — opcja kompilatora C#](keyfile-compiler-option.md)
- [Opcje kompilatora C#](index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
