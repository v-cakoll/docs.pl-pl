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
ms.openlocfilehash: e4558084357c8ce07004a8ed71aef586a707f1a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591750"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (opcje kompilatora C#)
**-Win32icon** opcja Wstawia plik .ico, w pliku danych wyjściowych, który nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik .ico, który chcesz dodać do pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
 Plik .ico, mogą być tworzone za pomocą [kompilator zasobów](/windows/desktop/menurc/resource-compiler). Kompilator zasobów jest wywoływane, gdy kompilujesz program Visual C++; plik .ico, który jest tworzony z pliku .rc.  
  
 Zobacz [- linkresource —](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (do odwołania) lub [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (Aby dołączyć) plikiem zasobów .NET Framework. Zobacz [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) można zaimportować plik res.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** stron.  
  
2.  Kliknij przycisk **aplikacji** stronę właściwości.  
  
3.  Modyfikowanie **ikony aplikacji** właściwości.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs` i dołączyć plik .ico `rf.ico` do produkcji `in.exe`:  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
