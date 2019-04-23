---
title: -unsafe (opcje kompilatora C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 4cfd7c82bc2cbf816164b235642c0647eeb7e5b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337334"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (opcje kompilatora C#)
**-Unsafe** — opcja kompilatora umożliwia kod, który używa [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe, aby skompilować.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat niebezpieczny kod, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz projekt **właściwości** strony.  
  
2. Kliknij przycisk **kompilacji** stronę właściwości.  
  
3. Wybierz **Zezwalaj na niebezpieczny kod** pole wyboru.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Aby dodać tę opcję w pliku csproj

Otwórz plik csproj projektu i dodaj następujące elementy:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs` dla trybu niebezpiecznego:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
