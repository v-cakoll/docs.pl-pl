---
title: 'Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
ms.openlocfilehash: ed4a818921f26fd5eb70fc4ba52929522627c096
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698209"
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)
W tym przykładzie pokazano, jak przyjaznych zestawów za pomocą zestawów, które są bez znaku.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Aby utworzyć zestaw i zestaw przyjazny  
  
1.  Otwórz wiersz polecenia.  
  
2.  Utwórz plik w języku Visual Basic o nazwie `friend_signed_A.` zawierający poniższy kod. Kod używa <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zadeklarować friend_signed_B jako przyjaznego zestawu.  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' vbc -target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  Skompiluj i podpisać friend_signed_A przy użyciu następującego polecenia.  
  
    ```console  
    vbc -target:library friend_unsigned_A.vb  
    ```  
  
4.  Utwórz plik w języku Visual Basic o nazwie `friend_unsigned_B` zawierający poniższy kod. Ponieważ friend_unsigned_A określa friend_unsigned_B jako zestaw przyjazny, kod w friend_unsigned_B mogą uzyskiwać dostęp do `Friend` typów i elementów członkowskich z friend_unsigned_A.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  Skompiluj friend_signed_B przy użyciu następującego polecenia.  
  
    ```console
    vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     Nazwa zestawu, który jest generowany przez kompilator musi odpowiadać nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Należy jawnie określić zestawu przy użyciu `/out` — opcja kompilatora.  
  
6.  Uruchom plik friend_signed_B.exe.  
  
     Ten program wyświetla dwa ciągi: "Class1.Test" i "Class2.Test".  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Istnieją podobieństwa między usługami <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu i <xref:System.Security.Permissions.StrongNameIdentityPermission> klasy. Główną różnicą jest to, że <xref:System.Security.Permissions.StrongNameIdentityPermission> może wymagać uprawnienia zabezpieczeń do uruchamiania w określonej sekcji kodu, natomiast <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut kontroluje widoczność `Friend` typów i elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [Przyjazne zestawy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)
- [Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Pojęcia związane z programowaniem przewodnik](../../../../visual-basic/programming-guide/concepts/index.md)
