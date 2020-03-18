---
title: -win32icon (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606274"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (Opcje kompilatora C#)
Opcja **-win32icon** wstawia plik .ico w pliku wyjściowym, co nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik .ico, który chcesz dodać do pliku wyjściowego.  
  
## <a name="remarks"></a>Uwagi  
 Plik .ico można utworzyć za pomocą [kompilatora zasobów](/windows/desktop/menurc/resource-compiler). Kompilator zasobów jest wywoływany podczas kompilowania programu Visual C++; plik .ico jest tworzony z pliku .rc.  
  
 Zobacz [-linkresource](./linkresource-compiler-option.md) (do odwołania) lub [-resource](./resource-compiler-option.md) (do dołączenia) plik zasobów .NET Framework. Zobacz [-win32res,](./win32res-compiler-option.md) aby zaimportować plik .res.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz strony **Właściwości** projektu.  
  
2. Kliknij stronę **właściwości Application.**  
  
3. Zmodyfikuj właściwość **Ikona aplikacji.**  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Skompiluj `in.cs` i dołącz `rf.ico` plik `in.exe`.ico do produkcji:  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
