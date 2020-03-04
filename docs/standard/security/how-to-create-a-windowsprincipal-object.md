---
title: 'Porady: tworzenie obiektu WindowsPrincipal'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: 30af18b7d7b86621586c7da66eda1b37356d5565
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159783"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Porady: tworzenie obiektu WindowsPrincipal
Istnieją dwa sposoby tworzenia obiektu <xref:System.Security.Principal.WindowsPrincipal>, w zależności od tego, czy kod musi wielokrotnie wykonywać walidację opartą na rolach, czy też musi wykonać tę operację tylko raz.  
  
 Jeśli kod musi wielokrotnie wykonywać walidację opartą na rolach, pierwsze z poniższych procedur generuje mniej kosztów. Gdy kod musi wprowadzać walidacje oparte na rolach tylko raz, można utworzyć obiekt <xref:System.Security.Principal.WindowsPrincipal> przy użyciu drugiej z poniższych procedur.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Aby utworzyć obiekt WindowsPrincipal do powtarzanej walidacji  
  
1. Wywołaj metodę <xref:System.AppDomain.SetPrincipalPolicy%2A> na obiekcie <xref:System.AppDomain>, który jest zwracany przez właściwość statycznej <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType>, przekazując metodę <xref:System.Security.Principal.PrincipalPolicy> wartość wyliczenia, która wskazuje, jakie nowe zasady powinny być. Obsługiwane wartości to <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>i <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Poniższy kod ilustruje to wywołanie metody.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. Mając zestaw zasad, użyj statycznej właściwości <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> do pobrania podmiotu zabezpieczeń, który hermetyzuje bieżącego użytkownika systemu Windows. Ponieważ typem zwracanym właściwości jest <xref:System.Security.Principal.IPrincipal>, należy rzutować wynik na typ <xref:System.Security.Principal.WindowsPrincipal>. Poniższy kod inicjuje nowy obiekt <xref:System.Security.Principal.WindowsPrincipal> do wartości podmiotu zabezpieczeń skojarzonego z bieżącym wątkiem.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. Po utworzeniu obiektu podmiotu zabezpieczeń można użyć jednej z kilku metod weryfikacji.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Aby utworzyć obiekt WindowsPrincipal na potrzeby pojedynczej walidacji  
  
1. Zainicjuj nowy obiekt <xref:System.Security.Principal.WindowsIdentity> przez wywołanie statycznej metody <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>, która wysyła zapytanie do bieżącego konta systemu Windows i umieszcza informacje o tym koncie w nowo utworzonym obiekcie tożsamości. Poniższy kod tworzy nowy obiekt <xref:System.Security.Principal.WindowsIdentity> i inicjuje go dla bieżącego uwierzytelnionego użytkownika.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Utwórz nowy obiekt <xref:System.Security.Principal.WindowsPrincipal> i przekaż go do wartości obiektu <xref:System.Security.Principal.WindowsIdentity> utworzonego w poprzednim kroku.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Po utworzeniu obiektu podmiotu zabezpieczeń można użyć jednej z kilku metod weryfikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
