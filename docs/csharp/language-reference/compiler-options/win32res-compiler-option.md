---
title: -win32res (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 4026fcbd7dc2ef29c1e7ee01a0f37b3ff471b187
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322385"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (opcje kompilatora C#)
**-Win32res** Opcja wstawia zasób Win32 w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobów, który chcesz dodać do pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
 Plik zasobów Win32 mogą być tworzone za pomocą [kompilator zasobów](../../language-reference/compiler-options/resource-compiler-option.md). Kompilator zasobów jest wywoływany podczas kompilacji programów Visual C++; plik .res jest tworzony z pliku .rc.  
  
 Zasób Win32 może zawierać wersji lub informacje mapy bitowej (ikonę), które może pomóc zidentyfikować aplikację w Eksploratorze plików. Jeśli nie określisz **-win32res**, kompilator wygeneruje informacje o wersji, w zależności od używanej wersji zestawu.  
  
 Zobacz [- linkresource —](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (do odwołania) lub [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (Aby dołączyć) plikiem zasobów .NET Framework.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz projekt **właściwości** strony.  
  
2. Kliknij przycisk **aplikacji** stronę właściwości.  
  
3. Kliknij pozycję **pliku zasobów** przycisku i wybierz plik za pomocą pola kombi.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs` i dołączyć plik zasobów Win32 `rf.res` do produkcji `in.exe`:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
