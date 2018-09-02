---
title: -resource (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: e02eda66ab9fadbc7b5b042c8940096c70ef6a03
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419554"
---
# <a name="-resource-c-compiler-options"></a>-resource (opcje kompilatora C#)
Osadza określony zasób w pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobu .NET Framework, którą chcesz osadzić w pliku wyjściowym.  
  
 `identifier` (opcjonalnie)  
 Nazwa logiczna zasobu; Nazwa która jest używana do ładowania zasobów. Wartość domyślna to nazwa pliku.  
  
 `accessibility-modifier` (opcjonalnie)  
 Dostępność zasobów: publicznych lub prywatnych. Wartość domyślna jest publiczny.  
  
## <a name="remarks"></a>Uwagi  
 Użyj [- linkresource —](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) łączenie zasobu z zestawem i nie należy dodać plik zasobów do pliku wyjściowego.  
  
 Zasoby są domyślnie publiczne w zestawie podczas ich tworzenia za pomocą kompilatora C#. Zasoby prywatne, ustaw `private` jako modyfikator dostępności metody dostępu. Nie innych ułatwień dostępu innym niż `public` lub `private` jest dozwolone.  
  
 Jeśli `filename` jest plikiem zasobów .NET Framework, utworzonym na przykład przez [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. W przypadku wszystkich innych zasobów, użyj `GetManifestResource` metody <xref:System.Reflection.Assembly> klasy, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 **-res** jest krótka forma **-resource**.  
  
 Kolejność zasobów w pliku danych wyjściowych jest określana na podstawie kolejności określonej w wierszu polecenia.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Dodaj plik zasobów do projektu.  
  
2.  Wybierz plik, który ma zostać osadzony w **Eksploratora rozwiązań**.  
  
3.  Wybierz **Build Action** dla pliku **właściwości** okna.  
  
4.  Ustaw **Akcja kompilacji** do **osadzony zasób**.  
  
 Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs` i dołączyć plik zasobów `rf.resource`:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
