---
title: -optimize (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606601"
---
# <a name="-optimize-c-compiler-options"></a>-optimize (Opcje kompilatora C#)
Opcja **-optimize** włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby zmniejszyć, przyspieszyć i wydajniej sprawić, że plik wyjściowy będzie mniejszy, szybszy i wydajniejszy.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 **-optimize** informuje również czas wykonywania języka wspólnego do optymalizacji kodu w czasie wykonywania.  
  
 Domyślnie optymalizacje są wyłączone. Określ **-optimize+,** aby włączyć optymalizacje.  
  
 Podczas tworzenia modułu, który ma być używany przez zespół, należy użyć tych samych ustawień **optymalizowania,** co ustawienia złożenia.  
  
 **-o** jest krótką formą **-optimize**.  
  
 Możliwe jest połączenie opcji **-optimize** i [-debug.](./debug-compiler-option.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. **Zmodyfikuj właściwość Optymalizuj kod.**  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Skompiluj `t2.cs` i włącz optymalizacje kompilatora:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
