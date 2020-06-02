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
ms.openlocfilehash: 6064c98c4e1e5153f4e0de4849de196228972a89
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284432"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Porady: tworzenie obiektu WindowsPrincipal
Istnieją dwa sposoby tworzenia <xref:System.Security.Principal.WindowsPrincipal> obiektu, w zależności od tego, czy kod musi wielokrotnie wykonywać walidację opartą na rolach, czy też musi wykonać tę operację tylko raz.  
  
 Jeśli kod musi wielokrotnie wykonywać walidację opartą na rolach, pierwsze z poniższych procedur generuje mniej kosztów. Gdy kod musi wprowadzać walidacje oparte na rolach tylko raz, można utworzyć <xref:System.Security.Principal.WindowsPrincipal> Obiekt przy użyciu drugiego z poniższych procedur.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Aby utworzyć obiekt WindowsPrincipal do powtarzanej walidacji  
  
1. Wywołaj <xref:System.AppDomain.SetPrincipalPolicy%2A> metodę dla <xref:System.AppDomain> obiektu, który jest zwracany przez właściwość statyczną <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> , przekazując metodę <xref:System.Security.Principal.PrincipalPolicy> wartości wyliczenia, która wskazuje, jakie nowe zasady powinny być. Obsługiwane wartości to <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal> , <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> , i <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal> . Poniższy kod ilustruje to wywołanie metody.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. Za pomocą zestawu zasad należy użyć właściwości statycznej <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> do pobrania podmiotu zabezpieczeń, który hermetyzuje bieżącego użytkownika systemu Windows. Ponieważ typem zwracanym właściwości jest <xref:System.Security.Principal.IPrincipal> , należy rzutować wynik na <xref:System.Security.Principal.WindowsPrincipal> Typ. Poniższy kod inicjuje nowy <xref:System.Security.Principal.WindowsPrincipal> obiekt do wartości podmiotu zabezpieczeń skojarzonego z bieżącym wątkiem.  
  
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
  
1. Zainicjuj nowy <xref:System.Security.Principal.WindowsIdentity> obiekt przez wywołanie metody statycznej <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> , która wysyła zapytanie do bieżącego konta systemu Windows i umieszcza informacje o tym koncie w nowo utworzonym obiekcie tożsamości. Poniższy kod tworzy nowy <xref:System.Security.Principal.WindowsIdentity> obiekt i inicjuje go dla bieżącego uwierzytelnionego użytkownika.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Utwórz nowy <xref:System.Security.Principal.WindowsPrincipal> obiekt i przekaż go do wartości <xref:System.Security.Principal.WindowsIdentity> obiektu utworzonego w poprzednim kroku.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Po utworzeniu obiektu podmiotu zabezpieczeń można użyć jednej z kilku metod weryfikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Obiekty główne i obiekty tożsamości](principal-and-identity-objects.md)
