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
ms.openlocfilehash: 5a7b378cad7a1df9249fcbefa28bb9aa9a6a3da4
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472571"
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
 Gdy **- keycontainer** jest używana opcja, kompilator tworzy zabezpieczać składnika. Kompilator wstawia klucza publicznego z kontenera określonej w manifeście zestawu i podpisuje zestawie końcowym z kluczem prywatnym. Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia. `sn -i` Instaluje pary kluczy do kontenera. Ta opcja nie jest obsługiwana, gdy kompilator uruchamia środowisko CoreCLR. Aby podpisać zestaw podczas kompilowania na środowisko CoreCLR, należy użyć [- keyfile](keyfile-compiler-option.md) opcji.
  
 Jeśli kompilacji z [-docelowych: moduł](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), nazwa pliku klucza jest przechowywana w module i wbudowanej w zestawie podczas kompilowania tego modułu do zestawu z [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Tę opcję można również określić jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) w kodzie źródłowym dla każdy moduł język pośredni (MSIL) firmy Microsoft.  
  
 Można również przekazać do kompilatora z informacjami szyfrowania [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Użyj [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli klucz publiczny dodane do manifestu zestawu, ale opóźnić podpisywania zestawu, dopóki nie był testowany.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Ta opcja kompilatora nie jest dostępna w środowisku programowania Visual Studio.  
  
 Programowo dostęp do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [-Keyfile — opcja kompilatora C#](keyfile-compiler-option.md) [opcje kompilatora C#](index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
