---
title: -warnaserror (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: a29b0a6095453e3d2747cad9d9f71b463d8f6b1f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733719"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (opcje kompilatora C#)
**- Warnaserror +** opcji traktuje wszystkie ostrzeżenia jako błędy  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie komunikaty, które zazwyczaj będzie zgłaszane jako ostrzeżenia zamiast tego są zgłaszane jako błędy, a proces kompilacji jest zatrzymana (Brak danych wyjściowych, które są tworzone pliki).  
  
 Domyślnie **- warnaserror —** obowiązują, co powoduje, że ostrzeżenia nie uniemożliwia generowanie pliku wyjściowego. **-warnaserror**, która jest taka sama jak **- warnaserror +**, powoduje, że ostrzeżenia są traktowane jako błędy.  
  
 Opcjonalnie Jeśli chcesz tylko kilka określone ostrzeżenia są traktowane jako błędy, można określić przecinkami lista numerów ostrzeżeń do traktowania jako błędy, które.  
  
 Użyj [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) określa poziom ostrzeżeń, które mają kompilatora do wyświetlenia. Użyj [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) można wyłączyć niektórych ostrzeżeń.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** stronę właściwości.  
  
3.  Modyfikowanie **Traktuj ostrzeżenia jako błędy** właściwości.  
  
 Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs` i pozwolić kompilatorowi wyświetlane nie ostrzeżenia:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
