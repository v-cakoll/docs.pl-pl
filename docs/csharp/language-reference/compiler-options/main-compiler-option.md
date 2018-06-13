---
title: -main (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2df02200578979f9a613f43dc92cc9e7b0cb430e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212423"
---
# <a name="-main-c-compiler-options"></a>-main (opcje kompilatora C#)
Ta opcja określa klasę, która zawiera wpis wskaż program, jeśli zawiera więcej niż jedną klasę **Main** metody.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Argumenty  
 `class`  
 Typ zawierający **Main** metody.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli Twoje kompilacji zawiera więcej niż jeden typ z [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody, można określić, którego typ zawiera **Main** metodę, która ma być używany jako punkt wejścia do programu.  
  
 Ta opcja jest przeznaczona do użytku podczas kompilowania pliku .exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **obiekt uruchomieniowy** właściwości.  
  
     Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t2.cs` i `t3.cs`, określania który **Main** będzie można znaleźć metody w `Test2`:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
