---
title: -optimize (opcje kompilatora C#)
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
ms.openlocfilehash: 86c8ebb2d2061085be4c00e8ac95448e1c341161
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-optimize-c-compiler-options"></a>-optimize (opcje kompilatora C#)
**-Zoptymalizować** opcja włącza lub wyłącza wykonywanie optymalizacji przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajne.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Uwagi  
 **-optimize** również informuje środowisko uruchomieniowe języka wspólnego do optymalizacji kodu w czasie wykonywania.  
  
 Optymalizacje są domyślnie wyłączone. Określ **-zoptymalizować +** do włączenia optymalizacji.  
  
 Podczas kompilowania modułu używanego przez zespół, należy używać tego samego **-zoptymalizować** ustawienia jak zestawu.  
  
 **-o** jest krótka forma **-zoptymalizować**.  
  
 Istnieje możliwość łączenia **— zoptymalizować** i [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) opcje.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Modyfikowanie **Optymalizuj kod** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t2.cs` i Włącz optymalizacje kompilatora:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
