---
title: -win32icon (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: ba5c7fcc8fe9e3eaab0a955f4cd1a1e07169049e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216206"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (opcje kompilatora C#)
**-Win32icon** opcja Wstawia plik .ico w pliku danych wyjściowych, który zawiera plik wyjściowy żądanego wyglądu w Eksploratorze plików.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik .ico, który chcesz dodać do pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
 Plik .ico mogą być tworzone za pomocą [kompilator zasobów](https://msdn.microsoft.com/library/aa381042.aspx). Kompilator zasobów jest wywoływane, gdy kompilacja programu Visual C++; plik .rc jest utworzony plik .ico.  
  
 Zobacz [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (do odwołania) lub [-zasobów](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (Aby dołączyć) plik zasobu .NET Framework. Zobacz [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) można zaimportować pliku .res.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** stron.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **ikona aplikacji** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i Dołącz plik .ico `rf.ico` do produkcji `in.exe`:  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
