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
ms.openlocfilehash: 14656fa25ea1d01339bd63efb999e938e1243db8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865611"
---
# <a name="-warn-c-compiler-options"></a>-warn (opcje kompilatora C#)
**-Warn** opcja określa poziom ostrzeżeń dla kompilatora do wyświetlenia.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Argumenty  
 `option`  
 Poziom ostrzeżeń, które mają być wyświetlane dla kompilacji: niższych numerach Pokaż tylko ostrzeżenia o wysokiej ważności; tymi o wyższych numerach Pokaż więcej ostrzeżeń. Prawidłowe wartości to 0-4:  
  
|Poziom ostrzeżeń|Znaczenie|  
|-------------------|-------------|  
|0|Wyłącza emisji wszystkie komunikaty ostrzegawcze.|  
|1|Wyświetla poważne ostrzeżenia.|  
|2|Wyświetla ostrzeżenia poziomu 1 oraz pewnym ostrzeżenia mniej poważne, takie jak ostrzeżenia o ukrywaniu składowych klasy.|  
|3|Wyświetla poziom ostrzeżeń 2 plus niektórych, ostrzeżenia mniej poważne, takie jak ostrzeżenia na temat wyrażeń, które zawsze przyjmowało `true` lub `false`.|  
|4 (ustawienie domyślne)|Wyświetla wszystkie poziom ostrzeżeń 3. oraz ostrzeżenia informacyjne.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje na temat błędu lub ostrzeżenia, możesz wyszukać kod błędu w indeksie Pomocy. Aby uzyskać inny sposób uzyskać informacje na temat błędu lub ostrzeżenia, zobacz [błędy kompilatora C#](../../../csharp/language-reference/compiler-messages/index.md).  
  
 Użyj [- warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) na traktowanie wszystkich ostrzeżeń jako błędy. Użyj [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) można wyłączyć niektórych ostrzeżeń.  
  
 **-w** jest krótka forma **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** stronę właściwości.  
  
3.  Modyfikowanie **poziom ostrzeżeń** właściwości.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs` i pozwolić kompilatorowi na tylko wyświetlania ostrzeżenia poziomu 1:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
