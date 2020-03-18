---
title: -win32res (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 39f02c4c2e060c4be40002a2f48b0da31004a9ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606199"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (Opcje kompilatora C#)
Opcja **-win32res** wstawia zasób Win32 do pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobów, który chcesz dodać do pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą [kompilatora zasobów](../../language-reference/compiler-options/resource-compiler-option.md)można utworzyć plik zasobu Win32 . Kompilator zasobów jest wywoływany podczas kompilacji programów Visual C++; plik .res jest tworzony z pliku .rc.  
  
 Zasób Win32 może zawierać informacje o wersji lub bitmap (ikonie), które mogłyby pomóc w identyfikacji aplikacji w Eksploratorze plików. Jeśli nie **określisz -win32res,** kompilator wygeneruje informacje o wersji na podstawie wersji zestawu.  
  
 Zobacz [-linkresource](./linkresource-compiler-option.md) (do odwołania) lub [-resource](./resource-compiler-option.md) (do dołączenia) plik zasobów .NET Framework.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **właściwości Application.**  
  
3. Kliknij przycisk **Plik zasobu** i wybierz plik przy użyciu pola kombi.  
  
## <a name="example"></a>Przykład  
 Skompiluj `in.cs` i dołącz plik `rf.res` zasobów `in.exe`Win32 do produkcji:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
