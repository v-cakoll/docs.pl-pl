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
ms.openlocfilehash: f8fec2c4da49aa6cac2f8dc1dc9b07c5864b837a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259957"
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
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** stronę właściwości.  
  
3.  Modyfikowanie **Optymalizuj kod** właściwości.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Przykład  
 Skompilować `t2.cs` i włączyć optymalizacje kompilatora:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
