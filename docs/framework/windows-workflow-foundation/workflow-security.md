---
title: Zabezpieczenia przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 2a9b26f8da7616480f69a6c4580b8d351833c9ee
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646321"
---
# <a name="workflow-security"></a>Zabezpieczenia przepływu pracy
Windows Workflow Foundation (WF) jest zintegrowany z kilkoma różnymi technologiami, takimi jak Microsoft SQL Server i Windows Communication Foundation (WCF). Interakcja z tymi technologiami może powodować problemy z zabezpieczeniami w przepływie pracy, jeśli zostanie wykonana nieprawidłowo.

## <a name="persistence-security-concerns"></a>Obawy dotyczące bezpieczeństwa trwałości

1. Przepływy pracy, <xref:System.Activities.Statements.Delay> które używają działania i trwałości muszą być ponownie aktywowane przez usługę. Usługa AppFabric systemu Windows używa usługi zarządzania przepływem pracy (WMS) do ponownego uaktywniania przepływów pracy przy użyciu wygasłych czasomierzy. Program WMS <xref:System.ServiceModel.WorkflowServiceHost> tworzy hosta ponownie uaktywnionego przepływu pracy. Jeśli usługa WMS zostanie zatrzymana, utrwalone przepływy pracy nie zostaną ponownie aktywowane po wygaśnięciu czasomierzy.

2. Dostęp do trwałego instancing powinny być chronione przed złośliwymi jednostkami zewnętrznymi domeny aplikacji. Ponadto deweloperzy powinni upewnić się, że złośliwy kod nie może być wykonywany w tej samej domenie aplikacji, co kod trwały.

3. Trwałe instancing nie powinny być uruchamiane z podwyższonym poziomem uprawnień (Administrator).

4. Dane przetwarzane poza domeną aplikacji powinny być chronione.

5. Aplikacje, które wymagają izolacji zabezpieczeń nie powinny współużytkuje tego samego wystąpienia abstrakcji schematu. Takie aplikacje powinny używać różnych dostawców magazynu lub dostawców magazynu skonfigurowanych do używania różnych wystąpienia magazynu.

## <a name="sql-server-security-concerns"></a>Problemy z zabezpieczeniami programu SQL Server

- Gdy używana jest duża liczba działań podrzędnych, lokalizacji, zakładek, rozszerzeń hosta lub zakresów lub gdy używane są zakładki z bardzo dużymi ładunkami, pamięć może zostać wyczerpana lub można przydzielić nadmierne ilości miejsca w bazie danych podczas trwałości. Można to złagodzić przy użyciu zabezpieczeń na poziomie obiektu i bazy danych.

- Podczas <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>korzystania magazyn wystąpień musi być zabezpieczony.

- Poufne dane w magazynie wystąpień powinny być szyfrowane. Aby uzyskać więcej informacji, zobacz [SQL Server Encryption](/sql/relational-databases/security/encryption/sql-server-encryption).

- Ponieważ parametry połączenia bazy danych są często zawarte w pliku konfiguracyjnym, zabezpieczenia na poziomie Windows (ACL) powinny być używane w celu zapewnienia, że plik konfiguracyjny (Web.Config zwykle) jest bezpieczny, a informacje o logowaniu i haśle nie są zawarte w ciągu połączenia. Zamiast tego należy używać uwierzytelniania systemu Windows między bazą danych a serwerem sieci web.

## <a name="considerations-for-workflowservicehost"></a>Zagadnienia dotyczące usługi WorkflowServiceHost

- Punkty końcowe programu Windows Communication Foundation (WCF) używane w przepływach pracy powinny być zabezpieczone. Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń WCF](../wcf/feature-details/security-overview.md).

- Autoryzację na poziomie hosta <xref:System.ServiceModel.ServiceAuthorizationManager>można zaimplementować za pomocą programu . Zobacz Jak: Aby uzyskać szczegółowe [informacje, zobacz Jak: Tworzenie menedżera autoryzacji niestandardowej dla usługi.](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)

- ServiceSecurityContext dla wiadomości przychodzącej jest również dostępny z wewnątrz przepływu pracy przez dostęp OperationContext.

## <a name="wf-security-pack-ctp"></a>Pakiet zabezpieczeń WF CTP
 Microsoft WF Security Pack community technology preview (CTP) 1 to zestaw działań i ich implementacji w oparciu o [Windows Workflow Foundation](index.md) w [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) i [Windows Identity Foundation (WIF)](https://docs.microsoft.com/previous-versions/dotnet/framework/security/index). Pakiet zabezpieczeń Microsoft WF CTP 1 zawiera zarówno działania, jak i ich projektantów, które ilustrują, jak łatwo włączyć różne scenariusze związane z zabezpieczeniami przy użyciu przepływu pracy, w tym:

1. Personifikowanie tożsamości klienta w przepływie pracy

2. Autoryzacja przepływu w pracy, taka jak PrincipalPermission i sprawdzanie poprawności oświadczeń

3. Uwierzytelnione wiadomości przy użyciu clientcredentials określonych w przepływie pracy, takich jak nazwa użytkownika/hasło lub token pobrany z usługi tokenu zabezpieczającego (STS)

4. Przesyłanie tokenu zabezpieczającego klienta do usługi zaplecza (delegowanie oparte na oświadczeniach) przy użyciu actas zaufania WS

Aby uzyskać więcej informacji i pobrać pakiet WF Security Pack CTP, zobacz: [WF Security Pack CTP](https://archive.codeplex.com/?p=wf)
