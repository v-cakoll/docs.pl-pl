---
title: -warn (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 65a6348bb0364d79ed0e69daf3a31ea7aa1bf8ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-warn-c-compiler-options"></a>-warn (opcje kompilatora C#)
**-Warn** opcji określa poziom ostrzeżenia kompilatora do wyświetlenia.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Argumenty  
 `option`  
 Poziom ostrzeżeń, które mają być wyświetlane dla kompilacji: niższych numerach Pokaż tylko ostrzeżenia o wysokim znaczeniu; wyższe numery Pokaż więcej ostrzeżenia. Prawidłowe wartości to 0-4:  
  
|Poziom ostrzeżeń|Znaczenie|  
|-------------------|-------------|  
|0|Wyłącza emisji wszystkie komunikaty ostrzegawcze.|  
|1|Wyświetla poważne ostrzeżenia.|  
|2|Wyświetla ostrzeżenia poziomu 1 oraz, niektóre ostrzeżenia mniej poważne, takie jak ostrzeżenia dotyczące ukrywania elementów członkowskich klasy.|  
|3|Wyświetla poziom ostrzeżenia 2 oraz niektórych, ostrzeżenia mniej poważne, takie jak ostrzeżenia dotyczące wyrażeń, które zawsze `true` lub `false`.|  
|4 (ustawienie domyślne)|Wyświetla wszystkie poziomu 3 ostrzeżenia oraz ostrzeżenia informacyjne.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje dotyczące błędów lub ostrzeżeń, można wyszukiwać kod błędu w indeksie Pomocy. Aby inne sposoby uzyskania informacji na temat błędu lub ostrzeżenia, zobacz [błędy kompilatora C#](../../../csharp/language-reference/compiler-messages/index.md).  
  
 Użyj [- warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) na traktowanie wszystkich ostrzeżeń jako błędy. Użyj [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) Aby wyłączyć określone ostrzeżenia.  
  
 **-w** jest krótka forma **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Modyfikowanie **poziom ostrzeżeń** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i mieć kompilatora tylko wyświetlić ostrzeżenia poziomu 1:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
