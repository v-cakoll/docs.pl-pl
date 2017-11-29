---
title: Przyjazne zestawy (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 20b8d4f2d58af510a28160d28e6ef740d293d835
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assemblies-c"></a>Przyjazne zestawy (C#)
A *przyjaznego zestawu* jest zestawie, do którego mogą uzyskać dostęp do innego zestawu [wewnętrzny](../../../../csharp/language-reference/keywords/internal.md) typy i składniki. Po zidentyfikowaniu zestawu jako zestawu friend, masz już Oznacz typy i składniki jako public je, aby były dostępne dla innych zestawów. Jest to szczególnie wygodne w następujących scenariuszach:  
  
-   Podczas przeprowadzania testów jednostkowych, po uruchomieniu testu kodu osobny zestaw, ponieważ wymaga dostępu do elementów członkowskich w zestawie testowane oznaczonych jako `internal` .  
  
-   Podczas tworzenia biblioteki klas i ma zostać dodany do biblioteki są zawarte w oddzielne zestawy, ale wymagają dostępu do elementów członkowskich w istniejących zestawów, które są oznaczone jako `internal` .  
  
## <a name="remarks"></a>Uwagi  
 Można użyć <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zidentyfikować jeden lub więcej zestawów przyjazne dla danego zestawu. W poniższym przykładzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut w zestawie A i zestawu Określa `AssemblyB` jako przyjaznego zestawu. Dzięki temu zestawu `AssemblyB` dostęp do wszystkich typów i członków w zestawie, które są oznaczone jako `internal`.  
  
> [!NOTE]
>  Podczas kompilowania zestawu (zestawu `AssemblyB`) będzie uzyskiwać dostęp wewnętrzne typy lub wewnętrzne elementy członkowskie z innego zestawu (zestawu *A*), należy jawnie określić nazwę pliku wyjściowego (.exe lub .dll) przy użyciu **/out** — opcja kompilatora. Jest to wymagane, ponieważ kompilator nie ma jeszcze wygenerowany nazwę zestawu, w którym jest ona tworzenie w czasie, który jest wiązany odwołań zewnętrznych. Aby uzyskać więcej informacji, zobacz [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .  
  
```csharp  
using System.Runtime.CompilerServices;  
using System;  
  
[assembly: InternalsVisibleTo("AssemblyB")]  
  
// The class is internal by default.  
class FriendClass  
{  
    public void Test()  
    {  
        Console.WriteLine("Sample Class");  
    }  
}  
  
// Public class that has an internal method.  
public class ClassWithFriendMethod  
{  
    internal void Test()  
    {  
        Console.WriteLine("Sample Method");  
    }  
  
}  
```  
  
 Tylko zestawy, które zostaną jawnie określone jako znajomych mogą uzyskiwać dostęp do `internal` typy i składniki. Na przykład, jeśli zestaw B jest przyjaznego zestawu A i zestawu odwołania do zestawu C B, C nie ma dostępu do `internal` typów w A.  
  
 Kompilator wykonuje pewne podstawowe sprawdzanie poprawności nazwy przyjaznego zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Jeśli zestaw *A* deklaruje *B* jako przyjaznego zestawu reguł sprawdzania poprawności, są następujące:  
  
-   Jeśli zestaw *A* jest silną nazwę zestawu *B* musi również być silnej nazwy. Nazwy przyjaznego zestawu, który jest przekazywany do atrybutu musi zawierać nazwę zestawu i klucz publiczny klucz silnej nazwy, który jest używany do podpisywania zestawu *B*.  
  
     Nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie może być silnej nazwy zestawu *B*: nie ma zestawu wersji, kultury, architektury lub token klucza publicznego.  
  
-   Jeśli zestaw *A* nie jest silnej nazwie, nazwy przyjaznego zestawu powinien zawierać tylko nazwę zestawu. Aby uzyskać więcej informacji, zobacz [porady: tworzenie niepodpisanych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Jeśli zestaw *B* jest silnej nazwie, należy określić klucz silnej nazwy zestawu *B* za pomocą ustawienie projektu lub wiersza polecenia `/keyfile` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [porady: tworzenie podpisanego przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Klasa udostępnia także możliwość udostępniania typów, z następującymi różnicami:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission>dotyczy poszczególnych typu przyjaznego zestawu dotyczy całego zestawu.  
  
-   Jeśli istnieją setki typów w zestawie *A* , który ma zostać udostępniona w zestawie *B*, należy dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> do wszystkich z nich. Jeśli używasz przyjaznego zestawu, wystarczy raz zadeklarować relacji friend.  
  
-   Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission>, typów, aby udostępnić musi być zadeklarowana jako publiczną. Jeśli używasz przyjaznego zestawu udostępnionego typy są deklarowane jako `internal`.  
  
 Informacje na temat dostępu zestawu `internal` typy i metody z pliku modułu (plik z rozszerzeniem modułu .netmodule), zobacz [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [Porady: tworzenie nieoznaczonych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [Porady: tworzenie oznaczonych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
