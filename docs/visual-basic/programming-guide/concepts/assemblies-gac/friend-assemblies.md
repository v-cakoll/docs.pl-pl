---
title: Przyjazne zestawy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
ms.openlocfilehash: 9b91f894f9b10c85eb322b4421fd0473335df7a3
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748157"
---
# <a name="friend-assemblies-visual-basic"></a>Przyjazne zestawy (Visual Basic)
A *przyjaznego zestawu* to zestaw, który mogą uzyskiwać dostęp do innego zestawu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) typów i elementów członkowskich. Po zidentyfikowaniu zestawu jako zestaw przyjazny, masz już Oznacz typy i elementy członkowskie jako publiczny je, aby były dostępne dla innych zestawów. Jest to szczególnie wygodne w następujących scenariuszach:  
  
-   Podczas testowania jednostek, gdy kod testowy jest uruchamiany osobny zestaw ale wymaga dostępu do składowych w zestawie poddawana testom, które są oznaczone jako `Friend`.  
  
-   Podczas tworzenia biblioteki klas i ma zostać dodany do biblioteki znajdują się w osobnych zestawach, ale wymagają dostępu do elementów członkowskich w istniejących zestawów, które są oznaczone jako `Friend`.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut do identyfikowania jeden lub więcej zestawów przyjaznego dla danego zestawu. W poniższym przykładzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu w zestawie A i określa zestaw `AssemblyB` jako przyjaznego zestawu. Dzięki temu zestaw `AssemblyB` dostęp do wszystkich typów i elementów członkowskich w zestawie, które są oznaczone jako `Friend`.  
  
> [!NOTE]
>  Gdy kompilujesz zestaw (zestaw `AssemblyB`) będzie uzyskiwać dostęp typy wewnętrzne lub wewnętrzne członków innego zestawu (zestaw *A*), należy jawnie określić nazwę pliku wyjściowego (.exe lub .dll), używając **/out** — opcja kompilatora. Jest to wymagane, ponieważ kompilator nie ma jeszcze wygenerować nazwę zestawu, który tworzysz w czasie, który jest wiązanie odwołań zewnętrznych. Aby uzyskać więcej informacji, zobacz [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports System  
<Assembly: InternalsVisibleTo("AssemblyB")>   
  
' Friend class.  
Friend Class FriendClass  
    Public Sub Test()  
        Console.WriteLine("Sample Class")  
    End Sub  
End Class  
  
' Public class with a Friend method.  
Public Class ClassWithFriendMethod  
    Friend Sub Test()  
        Console.WriteLine("Sample Method")  
    End Sub  
End Class  
```  
  
 Tylko zestawy, które zostaną jawnie określone, zgodnie z przyjaciółmi mogą uzyskiwać dostęp do `Friend` typów i elementów członkowskich. Na przykład, jeśli zestaw B jest przyjaznego zestawu A i C zestawu odwołania do zestawu B, C nie ma dostępu do `Friend` typów w A.  
  
 Kompilator wykonuje niektóre podstawowe sprawdzanie poprawności nazwy przyjaznego zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Jeśli zestaw *A* deklaruje *B* jako zestaw przyjaznych reguły sprawdzania poprawności są następujące:  
  
-   Jeśli zestaw *A* jest silną nazwę zestawu *B* również musi mieć silną nazwę. Nazwy przyjaznego zestawu, który jest przekazywany do atrybutu musi zawierać nazwę zestawu i klucz publiczny klucz silnej nazwy, który jest używany do podpisywania zestawu *B*.  
  
     Nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie może być silnej nazwy zestawu *B*: nie ma zestawu wersji, kultury, architektury lub token klucza publicznego.  
  
-   Jeśli zestaw *A* nie jest silną nazwę, nazwy przyjaznego zestawu powinna składać się wyłącznie nazwy zestawu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Jeśli zestaw *B* jest silną nazwę, należy określić klucz silnej nazwy zestawu *B* przy użyciu wiersza polecenia i ustawienie projektu `/keyfile` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Klasa udostępnia także możliwość udostępniania typów, z następującymi różnicami:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> ma zastosowanie do poszczególnych typu, gdy zestaw przyjazny, który ma zastosowanie do całego zestawu.  
  
-   Jeśli istnieją setki typów w zestawie *A* , którą chcesz udostępnić zestawu *B*, trzeba dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> do wszystkich z nich. Jeśli używasz zestaw przyjazny, wystarczy raz deklarowania relacji friend.  
  
-   Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, które chcesz udostępnić musi być zadeklarowana jako publiczne. Jeśli używasz zestaw przyjazny, udostępnione typy są deklarowane jako `Friend`.  
  
 Aby uzyskać informacje dotyczące dostępu do zestawu `Friend` typów i metod z pliku modułu (plik z rozszerzeniem .netmodule), zobacz [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md)
