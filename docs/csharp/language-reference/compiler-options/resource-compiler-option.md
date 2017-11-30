---
title: -resource (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 726956275436e22723bc32b98b2b8b7c7df5fb12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="resource-c-compiler-options"></a>/resource (opcje kompilatora C#)
Osadza określony zasób w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobu .NET Framework ma być osadzony w pliku wyjściowym.  
  
 `identifier`(opcjonalnie)  
 Nazwa logiczna zasobu; Nazwa, która jest używana do załadowania zasobu. Wartość domyślna to nazwą pliku.  
  
 `accessibility-modifier`(opcjonalnie)  
 Dostępność zasobu: publicznych lub prywatnych. Wartość domyślna jest publiczny.  
  
## <a name="remarks"></a>Uwagi  
 Użyj [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) Połącz zasób z zestawem i nie dodać pliku zasobu do pliku wyjściowego.  
  
 Domyślnie zasoby są publiczne w zestawie podczas ich tworzenia za pomocą kompilatora C#. Zasoby prywatny, ustaw `private` jako modyfikator dostępności. Nie inne dostępności innych niż `public` lub `private` jest dozwolone.  
  
 Jeśli `filename` to plik zasobu .NET Framework utworzone, na przykład przez [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Inne zasoby, można użyć `GetManifestResource` metod w <xref:System.Reflection.Assembly> klasę, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 **/ res** jest krótka forma **/Resource**.  
  
 Kolejność zasobów w pliku wyjściowym jest określana w kolejności określonej w wierszu polecenia.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Dodawanie pliku zasobu do projektu.  
  
2.  Wybierz plik, który ma zostać osadzony w **Eksploratora rozwiązań**.  
  
3.  Wybierz **Akcja kompilacji** pliku w **właściwości** okna.  
  
4.  Ustaw **Akcja kompilacji** do **osadzonego zasobu**.  
  
 Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i Dołącz plik zasobu `rf.resource`:  
  
```console  
csc /resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
