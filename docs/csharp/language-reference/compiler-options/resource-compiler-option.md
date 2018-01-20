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
ms.openlocfilehash: c20de499ae0fd5f8869c9b6e78a308fde9787ef9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-resource-c-compiler-options"></a>-resource (opcje kompilatora C#)
Osadza określony zasób w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
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
  
 **-res** jest krótka forma **-zasobów**.  
  
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
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
