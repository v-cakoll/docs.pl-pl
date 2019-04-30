---
title: Zabezpieczenia przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: a5a8d4d0d41efb7a255080994c8e18302d302447
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669241"
---
# <a name="workflow-security"></a>Zabezpieczenia przepływu pracy
Windows Workflow Foundation (WF) są zintegrowane z wielu różnych technologii, takich jak Microsoft SQL Server i Windows Communication Foundation (WCF). Interakcja z tych technologii może powodować problemy z zabezpieczeniami w Twój przepływ pracy, jeśli będą wykonywane niepoprawnie.

## <a name="persistence-security-concerns"></a>Trwałość obawy związane z bezpieczeństwem

1. Przepływy pracy korzystające z <xref:System.Activities.Statements.Delay> aktywności i stanu trwałego konieczności ponownej aktywacji przez usługę. Windows AppFabric korzysta z usługi zarządzania przepływu pracy (WMS) ponownie uaktywnić przepływów pracy za pomocą czasomierzy wygasłe. Tworzy WMS <xref:System.ServiceModel.WorkflowServiceHost> do hostowania ponownie uaktywnione przepływu pracy. Po zatrzymaniu usługi WMS, po upływie limitu czasu w ich zegary nie będzie reaktywowane utrwalonych przepływów pracy.

2. Dostęp do wystąpień trwałe powinny być chronione przed złośliwe podmioty zewnętrzne w stosunku do domeny aplikacji. Ponadto deweloperzy należy upewnić się, że złośliwy kod, nie można wykonać w tej samej domenie aplikacji jako trwałe kod wystąpień.

3. Trwałe wystąpień nie należy uruchamiać z podwyższonym poziomem uprawnień (Administrator).

4. Dane są przetwarzane spoza domeny aplikacji powinny być chronione.

5. Aplikacje, które wymagają izolacji zabezpieczeń nie powinny współużytkować to samo wystąpienie elementu abstrakcji schematu. Takich aplikacji należy użyć magazynu różnych dostawców, lub przechowywać dostawców skonfigurowany do używania innego magazynu wystąpień.

## <a name="sql-server-security-concerns"></a>SQL Server Security Concerns

- Podczas korzystania z dużą liczbą działania podrzędne, lokalizacji, zakładek, rozszerzenia hosta lub zakresów lub stosowania zakładek z ładunkami bardzo duże, może dojść do wyczerpania pamięci lub nadmiernej ilości miejsca w bazie danych mogą być przydzielone w trwałości. Można to zminimalizować przy użyciu zabezpieczeń na poziomie bazy danych i na poziomie obiektu.

- Korzystając z <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, musi zostać zabezpieczony magazyn wystąpienia. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące serwera SQL](https://go.microsoft.com/fwlink/?LinkId=164972).

- Należy można zaszyfrować poufnych danych w magazynie wystąpienia. Aby uzyskać więcej informacji, zobacz [szyfrowania zabezpieczeń SQL](https://go.microsoft.com/fwlink/?LinkId=164976).

- Ponieważ parametry połączenia bazy danych, często znajduje się w pliku konfiguracji, zabezpieczenia na poziomie systemu windows (ACL) powinien być używany do zapewnienia, że plik konfiguracyjny (zwykle w pliku Web.Config) jest bezpieczna i informacje logowania i hasła nie są objęte Parametry połączenia. Uwierzytelnianie Windows należy użyć między bazy danych i serwera sieci web.

## <a name="considerations-for-workflowservicehost"></a>Considerations for WorkflowServiceHost

- Powinny być zabezpieczone punkty końcowe usług Windows Communication Foundation (WCF) używane w przepływach pracy. Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń programu WCF](https://go.microsoft.com/fwlink/?LinkID=164975).

- Uwierzytelnianie na poziomie hosta można zaimplementować przy użyciu <xref:System.ServiceModel.ServiceAuthorizationManager>. Zobacz [jak: Tworzenie Menedżera autoryzacji niestandardowej dla usługi](https://go.microsoft.com/fwlink/?LinkId=192228) Aby uzyskać szczegółowe informacje.

- ServiceSecurityContext komunikatu przychodzącego jest również dostępne z poziomu przepływów pracy, uzyskując dostęp do elementu OperationContext.

## <a name="wf-security-pack-ctp"></a>Pakiet zabezpieczeń WF CTP
 Microsoft WF zabezpieczeń pakietu CTP 1 jest pierwsza wersja zapoznawcza (CTP) technologii społeczności zestawu działań i ich wdrażania w oparciu o [Windows Workflow Foundation](index.md) w [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF (4) i [Windows Identity Foundation (WIF)](../security/index.md).  Microsoft WF zabezpieczeń Pack CTP 1 zawiera zarówno działań, jak i ich projektantów, które pokazują, jak łatwo automatyzować różne scenariusze związane z zabezpieczeniami, za pomocą przepływu pracy, w tym:

1. Personifikacja tożsamości klienta, w przepływie pracy

2. Autoryzacji w przepływie pracy, takich jak PrincipalPermission i weryfikacji oświadczeń

3. Wiadomości uwierzytelnione przy użyciu ClientCredentials określone w przepływie pracy, takie jak nazwa użytkownika/hasło lub token pobierane z Usługa tokenu zabezpieczającego (STS)

4. Prowadząca do tokenu zabezpieczeń klienta z usługą zaplecza (delegacji opartej na oświadczeniach) za pomocą usługi WS-Trust ActAs

Aby uzyskać więcej informacji i Pobierz CTP pakietu programu WF zabezpieczeń zobacz: [Pakiet zabezpieczeń WF CTP](https://archive.codeplex.com/?p=wf)