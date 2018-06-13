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
ms.openlocfilehash: 3f7f5f323006024c393cb066284712ed60836372
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216768"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (opcje kompilatora C#)
**-Win32res** Opcja wstawia zasobów Win32 w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobu, który chcesz dodać do pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
 Plik zasobów Win32 mogą być tworzone za pomocą [kompilator zasobów](../../language-reference/compiler-options/resource-compiler-option.md). Kompilator zasobów jest wywoływany podczas kompilacji programów Visual C++; plik .res jest tworzony z pliku .rc.  
  
 Zasób Win32 może zawierać wersji lub mapy bitowej (ikona) informacje, które może pomóc w identyfikacji aplikacji w Eksploratorze plików. Jeśli nie określisz **-win32res**, kompilator generuje informacje o wersji, w zależności od używanej wersji zestawu.  
  
 Zobacz [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (do odwołania) lub [-zasobów](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (Aby dołączyć) plik zasobu .NET Framework.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Polecenie **pliku zasobu** przycisk i wybierz plik przy użyciu pola kombi.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i Dołącz plik zasobów Win32 `rf.res` do produkcji `in.exe`:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
