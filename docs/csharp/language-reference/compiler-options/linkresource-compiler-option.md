---
title: -linkresource (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d478c42141288cc3a1478ecf43f50c961a9d2246
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-c-compiler-options"></a>/linkresource (opcje kompilatora C#)
Tworzy łącze do zasobu .NET Framework w pliku wyjściowym. Plik zasobu nie została dodana do pliku wyjściowego. To różni się od [/Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) opcję, która osadzić pliku zasobów w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobu .NET Framework, do którego chcesz połączyć z zestawu.  
  
 `identifier`(opcjonalnie)  
 Nazwa logiczna zasobu; Nazwa, która jest używana do załadowania zasobu. Wartość domyślna to nazwa pliku.  
  
 `accessibility-modifier`(opcjonalnie)  
 Dostępność zasobu: publicznych lub prywatnych. Wartość domyślna jest publiczny.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie połączonych zasobów są publicznie udostępniane w zestawie, tworzona przez kompilator języka C#. Zasoby prywatny, ustaw `private` jako modyfikator dostępności. Nie inne modyfikator innych niż `public` lub `private` jest dozwolone.  
  
 **/ linkresource** wymaga jednego z [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcje inne niż **/target: module**.  
  
 Jeśli `filename` to plik zasobu .NET Framework utworzone, na przykład przez [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Inne zasoby, można użyć `GetManifestResource` metod w <xref:System.Reflection.Assembly> klasę, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 Plik określony w `filename` może być dowolnym formacie. Na przykład można ustawić natywnej biblioteki DLL częścią zestawu, dzięki czemu mogą być zainstalowane w globalnej pamięci podręcznej zestawów i dostępne z kodu zarządzanego w zestawie. Drugi poniższych przykładach pokazano, jak to zrobić. Można tak samo postąpić w konsolidator zestawów. Trzeci poniższych przykładach pokazano, jak to zrobić. Aby uzyskać więcej informacji, zobacz [Al.exe (konsolidator zestawów)](../../../framework/tools/al-exe-assembly-linker.md) i [Praca z zestawami i Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **/ Linkres** jest krótka forma **/linkresource**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i łącza do pliku zasobów `rf.resource`:  
  
```console  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Przykład  
 Kompiluj `A.cs` do biblioteki DLL, łącze do natywnej N.dll biblioteki DLL i umieść dane wyjściowe w globalnej pamięci podręcznej zestawów (GAC). W tym przykładzie zarówno A.dll i N.dll będzie znajdować się w pamięci GAC.  
  
```console  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest to samo, jak poprzedni, ale przy użyciu opcji Assembly Linker.  
  
```console  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Al.exe (konsolidator zestawów)](../../../framework/tools/al-exe-assembly-linker.md)  
 [Praca z zestawami i Globalna pamięć podręczna zestawów](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
