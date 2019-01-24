---
title: Zabezpieczenia integracji CLR w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: af3ec1f8dba375082a9838f10fa63c9348f725b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681056"
---
# <a name="clr-integration-security-in-sql-server"></a>Zabezpieczenia integracji CLR w programie SQL Server
Microsoft SQL Server zapewnia integrację składnika wspólnego języka wspólnego (CLR) programu .NET Framework. Integracja środowiska CLR umożliwia pisanie procedur składowanych, wyzwalaczy, typy zdefiniowane przez użytkownika, funkcje zdefiniowane przez użytkownika, agregacje zdefiniowane przez użytkownika i przesyłania strumieniowego funkcje wartościami przechowywanymi w tabeli, w dowolnym języku .NET Framework, takich jak Microsoft Visual Basic .NET lub Microsoft Visual C#.  
  
 Środowisko CLR obsługuje model zabezpieczeń o nazwie zabezpieczenia dostępu kodu (CAS) dla kodu zarządzanego. W tym modelu uprawnienia są przyznawane zestawów w oparciu o dowody dostarczone przez kod w metadanych. Program SQL Server integruje modelu zabezpieczeń opartych na użytkownika programu SQL Server z modelem zabezpieczeń dostępu kodu środowiska CLR.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji na temat integracji CLR z programem SQL Server zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia dostępu kodu](../../../../../docs/framework/misc/code-access-security.md)|Zawiera tematy opisujące urzędów certyfikacji w programie .NET Framework.|  
|[Zabezpieczenia integracji CLR](/sql/relational-databases/clr-integration/security/clr-integration-security)|W tym artykule omówiono model zabezpieczeń dla kodu zarządzanego wykonania wewnątrz programu SQL Server.|  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)
- [Omówienie ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)
