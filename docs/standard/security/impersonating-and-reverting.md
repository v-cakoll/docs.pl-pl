---
title: Personifikacja i przywracanie
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: 14b01ec3ac800abd795e87b641a442df100f102b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706022"
---
# <a name="impersonating-and-reverting"></a>Personifikacja i przywracanie
Czasami może być konieczne uzyskanie tokenu konta systemu Windows w celu personifikacji konta systemu Windows. Na przykład aplikacja oparta na ASP.NET może wymagać działania w imieniu kilku użytkowników w różnym czasie. Aplikacja może zaakceptować token, który reprezentuje administratora Internet Information Services (IIS), spersonifikować tego użytkownika, wykonać operację i przywrócić poprzednią tożsamość. Następnie może zaakceptować token z usług IIS, który reprezentuje użytkownika o mniejszej liczbie praw, wykonanie jakiejś operacji i przywrócenie.  
  
 W sytuacjach, w których aplikacja musi personifikować konto systemu Windows, które nie zostało dołączone do bieżącego wątku przez usługi IIS, należy pobrać token tego konta i użyć go w celu aktywowania konta. Można to zrobić, wykonując następujące zadania:  
  
1. Pobierz token konta dla określonego użytkownika, wykonując wywołanie do niezarządzanej metody **funkcji LogonUser** . Ta metoda nie znajduje się w bibliotece klas podstawowych .NET Framework, ale znajduje się w niezarządzanej **advapi32. dll**. Uzyskiwanie dostępu do metod w kodzie niezarządzanym jest operacją zaawansowaną i wykracza poza zakres tej dyskusji. Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md). Aby uzyskać więcej informacji na temat metody **funkcji LogonUser** i **advapi32. dll**, zobacz dokumentację zestawu SDK platformy.  
  
2. Utwórz nowe wystąpienie klasy **WindowsIdentity** , przekazując token. Poniższy kod ilustruje to wywołanie, gdzie `hToken` reprezentuje token systemu Windows.  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. Rozpocznij personifikację, tworząc nowe wystąpienie klasy <xref:System.Security.Principal.WindowsImpersonationContext> i inicjując je za pomocą metody <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> zainicjowanej klasy, jak pokazano w poniższym kodzie.  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. Gdy nie ma już potrzeby personifikacji, wywołaj metodę <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType>, aby przywrócić personifikację, jak pokazano w poniższym kodzie.  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 Jeśli zaufany kod ma już dołączony obiekt <xref:System.Security.Principal.WindowsPrincipal> do wątku, można wywołać metodę **personifikacji**metody wystąpienia, która nie przyjmuje tokenu konta. Należy zauważyć, że jest to przydatne tylko wtedy, gdy obiekt **WindowsPrincipal** na wątku reprezentuje użytkownika innego niż ten, w którym proces jest aktualnie wykonywany. Na przykład może wystąpić taka sytuacja przy użyciu ASP.NET z włączonym uwierzytelnianiem systemu Windows, a Personifikacja jest wyłączona. W takim przypadku proces jest uruchamiany na koncie skonfigurowanym w Internet Information Services (IIS), podczas gdy bieżący podmiot zabezpieczeń reprezentuje użytkownika systemu Windows, który uzyskuje dostęp do strony.  
  
 Należy pamiętać, że nie należy **personifikować** ani **cofnąć** zmian obiektu **podmiotu zabezpieczeń** (<xref:System.Security.Principal.IPrincipal>) skojarzonego z bieżącym kontekstem wywołania. Zamiast tego personifikacja i wycofywanie zmienia token skojarzony z bieżącym procesem systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
- [Współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md)
