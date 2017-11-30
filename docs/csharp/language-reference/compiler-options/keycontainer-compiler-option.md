---
title: -keycontainer (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0292ff38b1d03f5960a20858fbb9c42a6aff1f43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="keycontainer-c-compiler-options"></a>/keycontainer (opcje kompilatora C#)
Określa nazwę kontenera kluczy kryptograficznych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a>Argumenty  
 `string`  
 Nazwa kontenera klucza silnej nazwy.  
  
## <a name="remarks"></a>Uwagi  
 Gdy **/KeyContainer** jest używana opcja, kompilator tworzy składnik zabezpieczać wstawianie klucza publicznego z kontenera określonej w manifeście zestawu i podpisywania z kluczem prywatnym zestawie końcowym. Aby wygenerować plik klucza, wpisz sn -k `file` w wierszu polecenia. SN -i instaluje pary kluczy do kontenera.  
  
 Jeśli kompilacji z [/target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), nazwa pliku klucza jest przechowywana w module i wbudowanej w zestawie podczas kompilowania tego modułu do zestawu z [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Tę opcję można również określić jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) w kodzie źródłowym dla każdy moduł język pośredni (MSIL) firmy Microsoft.  
  
 Można również przekazać do kompilatora z informacjami szyfrowania [/KeyFile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Użyj [/DelaySign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli klucz publiczny dodane do manifestu zestawu, ale opóźnić podpisywania zestawu, dopóki nie był testowany.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Ta opcja kompilatora nie jest dostępna w środowisku programowania Visual Studio.  
  
 Programowo dostęp do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
