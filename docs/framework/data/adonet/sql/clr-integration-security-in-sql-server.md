---
title: Zabezpieczenia integracji CLR w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 4756d13ff52a4c55b48c3ea56d26111029c8a7e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794558"
---
# <a name="clr-integration-security-in-sql-server"></a>Zabezpieczenia integracji CLR w programie SQL Server
Microsoft SQL Server zapewnia integrację składnika środowiska uruchomieniowego języka wspólnego (CLR) .NET Framework. Integracja środowiska CLR pozwala pisać procedury składowane, wyzwalacze, typy zdefiniowane przez użytkownika, funkcje zdefiniowane przez użytkownika, agregacje zdefiniowane przez użytkownika i funkcję przesyłania strumieniowego z wartościami przechowywanymi w tabeli przy użyciu dowolnego .NET Framework języka, takiego jak Microsoft Visual Basic .NET lub Microsoft Wizualizacja C#.  
  
 Środowisko CLR obsługuje model zabezpieczeń o nazwie zabezpieczenia dostępu kodu (CAS) dla kodu zarządzanego. W tym modelu uprawnienia są przyznawane zestawom w oparciu o dowody dostarczone przez kod w metadanych. SQL Server integruje model zabezpieczeń oparty na użytkownikach SQL Server z modelem zabezpieczeń opartym na kodzie w środowisku CLR.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji na temat integracji środowiska CLR z SQL Server, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia dostępu kodu](../../../misc/code-access-security.md)|Zawiera tematy opisujące urzędy certyfikacji w .NET Framework.|  
|[Zabezpieczenia integracji środowiska CLR](/sql/relational-databases/clr-integration/security/clr-integration-security)|Omawia model zabezpieczeń dla kodu zarządzanego wykonywanego wewnątrz SQL Server.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server](sql-server-common-language-runtime-integration.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
