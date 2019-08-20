---
title: -win32res — (C# opcje kompilatora)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606199"
---
# <a name="-win32res-c-compiler-options"></a>-win32res — (C# opcje kompilatora)
Opcja **-win32res —** wstawia zasób Win32 do pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobu, który ma zostać dodany do pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
 Plik zasobów Win32 można utworzyć za pomocą [kompilatora zasobów](../../language-reference/compiler-options/resource-compiler-option.md). Kompilator zasobów jest wywoływany podczas kompilacji programów Visual C++; plik .res jest tworzony z pliku .rc.  
  
 Zasób Win32 może zawierać informacje o wersji lub mapie bitowej (ikony), które ułatwią zidentyfikowanie aplikacji w Eksploratorze plików. Jeśli nie określisz **win32res —** , kompilator generuje informacje o wersji na podstawie wersji zestawu.  
  
 Zobacz [-linkresource —](./linkresource-compiler-option.md) (to Reference) lub [-Resource](./resource-compiler-option.md) (aby dołączyć) .NET Framework plik zasobów.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę właściwości **aplikacji** .  
  
3. Kliknij przycisk **plik zasobów** , a następnie wybierz plik za pomocą pola kombi.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i Dołącz plik `rf.res` zasobów Win32 do produkcji `in.exe`:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
