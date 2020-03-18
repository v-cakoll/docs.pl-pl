---
title: -niebezpieczne (opcje kompilatora C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877990"
---
# <a name="-unsafe-c-compiler-options"></a>-niebezpieczne (opcje kompilatora C#)

**Opcja -unsafe** kompilator umożliwia kod, który używa [niebezpiecznego](../keywords/unsafe.md) słowa kluczowego do kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat niebezpiecznego kodu, zobacz [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. Zaznacz pole wyboru **Zezwalaj na niebezpieczny kod.**  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Aby dodać tę opcję w pliku csproj

Otwórz plik csproj dla projektu i dodaj następujące elementy:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>opcji kompilatora, zobacz .  
  
## <a name="example"></a>Przykład

Skompiluj `in.cs` dla trybu niebezpiecznego:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
