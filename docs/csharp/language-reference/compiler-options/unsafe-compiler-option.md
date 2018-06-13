---
title: -unsafe (opcje kompilatora C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: e308cae4a46efd53a77baf5b175e9069b5371fa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214042"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (opcje kompilatora C#)
**-Unsafe** — opcja kompilatora umożliwia kodu korzystającego z [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe do skompilowania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat niebezpieczny kod, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Wybierz **Zezwalaj niebezpieczny kod** pole wyboru.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Aby dodać tę opcję w plik csproj

Otwórz pliku .csproj dla projektu i dodaj następujące elementy:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` dla trybu niebezpiecznego:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
