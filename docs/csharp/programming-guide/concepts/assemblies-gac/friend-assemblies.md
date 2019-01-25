---
title: Przyjazne zestawy (C#)
ms.date: 07/20/2015
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: e464162f12fe386c37262753331635ea82b128b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576983"
---
# <a name="friend-assemblies-c"></a>Przyjazne zestawy (C#)
A *przyjaznego zestawu* to zestaw, który mogą uzyskiwać dostęp do innego zestawu [wewnętrzny](../../../../csharp/language-reference/keywords/internal.md) typów i elementów członkowskich. Po zidentyfikowaniu zestawu jako zestaw przyjazny, masz już Oznacz typy i elementy członkowskie jako publiczny je, aby były dostępne dla innych zestawów. Jest to szczególnie wygodne w następujących scenariuszach:  
  
-   Podczas testowania jednostek, gdy kod testowy jest uruchamiany osobny zestaw ale wymaga dostępu do składowych w zestawie poddawana testom, które są oznaczone jako `internal` .  
  
-   Podczas tworzenia biblioteki klas i ma zostać dodany do biblioteki znajdują się w osobnych zestawach, ale wymagają dostępu do elementów członkowskich w istniejących zestawów, które są oznaczone jako `internal` .  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut do identyfikowania jeden lub więcej zestawów przyjaznego dla danego zestawu. W poniższym przykładzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu w zestawie A i określa zestaw `AssemblyB` jako przyjaznego zestawu. Dzięki temu zestaw `AssemblyB` dostęp do wszystkich typów i elementów członkowskich w zestawie, które są oznaczone jako `internal`.  
  
> [!NOTE]
>  Gdy kompilujesz zestaw (zestaw `AssemblyB`) będzie uzyskiwać dostęp typy wewnętrzne lub wewnętrzne członków innego zestawu (zestaw *A*), należy jawnie określić nazwę pliku wyjściowego (.exe lub .dll), używając **/out** — opcja kompilatora. Jest to wymagane, ponieważ kompilator nie ma jeszcze wygenerować nazwę zestawu, który tworzysz w czasie, który jest wiązanie odwołań zewnętrznych. Aby uzyskać więcej informacji, zobacz [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .  
  
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
  
 Tylko zestawy, które zostaną jawnie określone, zgodnie z przyjaciółmi mogą uzyskiwać dostęp do `internal` typów i elementów członkowskich. Na przykład, jeśli zestaw B jest przyjaznego zestawu A i C zestawu odwołania do zestawu B, C nie ma dostępu do `internal` typów w A.  
  
 Kompilator wykonuje niektóre podstawowe sprawdzanie poprawności nazwy przyjaznego zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Jeśli zestaw *A* deklaruje *B* jako zestaw przyjaznych reguły sprawdzania poprawności są następujące:  
  
-   Jeśli zestaw *A* jest silną nazwę zestawu *B* również musi mieć silną nazwę. Nazwy przyjaznego zestawu, który jest przekazywany do atrybutu musi zawierać nazwę zestawu i klucz publiczny klucz silnej nazwy, który jest używany do podpisywania zestawu *B*.  
  
     Nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie może być silnej nazwy zestawu *B*: nie ma zestawu wersji, kultury, architektury lub token klucza publicznego.  
  
-   Jeśli zestaw *A* nie jest silną nazwę, nazwy przyjaznego zestawu powinna składać się wyłącznie nazwy zestawu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie nieoznaczonych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Jeśli zestaw *B* jest silną nazwę, należy określić klucz silnej nazwy zestawu *B* przy użyciu wiersza polecenia i ustawienie projektu `/keyfile` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie oznaczonych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Klasa udostępnia także możliwość udostępniania typów, z następującymi różnicami:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> ma zastosowanie do poszczególnych typu, gdy zestaw przyjazny, który ma zastosowanie do całego zestawu.  
  
-   Jeśli istnieją setki typów w zestawie *A* , którą chcesz udostępnić zestawu *B*, trzeba dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> do wszystkich z nich. Jeśli używasz zestaw przyjazny, wystarczy raz deklarowania relacji friend.  
  
-   Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, które chcesz udostępnić musi być zadeklarowana jako publiczne. Jeśli używasz zestaw przyjazny, udostępnione typy są deklarowane jako `internal`.  
  
 Aby uzyskać informacje dotyczące dostępu do zestawu `internal` typów i metod z pliku modułu (plik z rozszerzeniem .netmodule), zobacz [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
