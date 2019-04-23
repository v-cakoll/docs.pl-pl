---
title: -Optymalizuj (opcje kompilatora C#)
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
ms.openlocfilehash: 25a9ee1b27836dfb00dcbc72712ed068639fa2fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320035"
---
# <a name="-optimize-c-compiler-options"></a>-Optymalizuj (opcje kompilatora C#)
**— Optymalizacja** opcja włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajne.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 **-Optymalizuj** informacje o tym, środowisko uruchomieniowe języka wspólnego do optymalizacji kodu w czasie wykonywania.  
  
 Domyślnie są wyłączone optymalizacje. Określ **— Optymalizacja +** Aby włączyć optymalizacje.  
  
 Podczas kompilowania modułu, który będzie używany przez zespół, należy używać tego samego **— Optymalizacja** ustawienia zgodnie z tymi zestawu.  
  
 **-o** jest krótka forma **— Optymalizacja**.  
  
 Można połączyć **— Optymalizacja** i [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) opcje.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz projekt **właściwości** strony.  
  
2. Kliknij przycisk **kompilacji** stronę właściwości.  
  
3. Modyfikowanie **Optymalizuj kod** właściwości.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Przykład  
 Skompilować `t2.cs` i włączyć optymalizacje kompilatora:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
