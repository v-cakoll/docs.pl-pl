---
title: Personifikacja i przywracanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 869b9aadfa236a39d9807062e61046922e382d13
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="impersonating-and-reverting"></a>Personifikacja i przywracanie
Czasami może być konieczne uzyskanie tokenu konta systemu Windows do personifikacji konta systemu Windows. Na przykład aplikacja oparty na programie ASP.NET może być konieczne działają w imieniu kilku użytkowników w różnym czasie. Aplikacja może akceptuje token, który reprezentuje administrator z Internet Information Services (IIS), personifikacji tego użytkownika w trakcie operacji i powrócić do poprzedniej tożsamości. Następnie go może zaakceptować tokenu z usług IIS, które reprezentuje użytkownika z prawami mniej, niektórych operacji i przywrócić ponownie.  
  
 W sytuacjach, w którym musi być Personifikowane przez aplikację konto systemu Windows, który nie został dołączony do bieżącego wątku przez usługi IIS należy pobrać token tego konta i użyj go, aby aktywować konto. Można to zrobić, wykonując następujące czynności:  
  
1.  Pobrać tokenu konta dla danego użytkownika poprzez wywołanie niezarządzanej **funkcji LogonUser** metody. Ta metoda nie jest w bibliotece programu .NET Framework klasy podstawowej, ale znajduje się w niezarządzanej **advapi32.dll**. Uzyskiwanie dostępu do metody za pomocą kodu niezarządzanego jest zaawansowanym działaniem i wykracza poza zakres tej dyskusji. Aby uzyskać więcej informacji, zobacz [współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md). Aby uzyskać więcej informacji na temat **funkcji LogonUser** — metoda i **advapi32.dll**, można znaleźć w dokumentacji zestawu SDK platformy.  
  
2.  Utwórz nowe wystąpienie klasy **WindowsIdentity** klasy, przekazując tokenu. Poniższy kod ilustruje to wywołanie, gdy `hToken` reprezentuje token systemu Windows.  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  Rozpocznij personifikacji, tworząc nowe wystąpienie klasy <xref:System.Security.Principal.WindowsImpersonationContext> klasy i Inicjowanie za pomocą <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> metody klasy zainicjowane, jak pokazano w poniższym kodzie.  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  Jeśli nie jest już potrzebne personifikacji, wywołaj <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> metodę, aby przywrócić personifikacji, jak pokazano w poniższym kodzie.  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 Jeśli zaufany kod został już dołączony <xref:System.Security.Principal.WindowsPrincipal> obiektów w wątku, należy wywołać metodę wystąpienia **Impersonate**, nie ma tokenu konta. Należy pamiętać, że jest to przydatne tylko kiedy **WindowsPrincipal** obiektu w wątku reprezentuje użytkownika innego niż ten, w którym proces jest aktualnie wykonywany. Na przykład może wystąpić sytuacja przy użyciu platformy ASP.NET z uwierzytelniania systemu Windows, włączona i personifikacji wyłączone. W takim przypadku proces działa w ramach konta skonfigurowane w Internet Information Services (IIS), podczas gdy bieżący podmiot zabezpieczeń reprezentuje użytkownika systemu Windows, który uzyskuje dostęp do strony.  
  
 Należy pamiętać, że ani **personifikacji** ani **Cofnij** zmiany **główna** obiektu (<xref:System.Security.Principal.IPrincipal>) skojarzone z bieżącego kontekstu wywołania. Zamiast personifikacja i przywracanie zmiany token skojarzone z bieżącego procesu systemu operacyjnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.Security.Principal.WindowsImpersonationContext>  
 [Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)  
 [Współdziałanie z kodem niezarządzanym](../../../docs/framework/interop/index.md)
