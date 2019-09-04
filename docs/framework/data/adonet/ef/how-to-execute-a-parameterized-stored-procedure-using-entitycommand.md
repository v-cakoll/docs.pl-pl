---
title: 'Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej procedury składowanej przy użyciu EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: a2196be1a5fb6b9c676542ab5bcc74b1824df9cc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251524"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej procedury składowanej przy użyciu EntityCommand
W tym temacie przedstawiono sposób wykonywania sparametryzowanej procedury składowanej przy użyciu <xref:System.Data.EntityClient.EntityCommand> klasy.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1. Dodaj [model szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
2. Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Zaimportuj procedurę `CourseGrade` składowanąiokreśljednostkijakotypzwracany.`GetStudentGrades` Aby uzyskać informacje na temat sposobu importowania procedury składowanej, [zobacz How to: Importuj procedurę](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100))składowaną.  
  
## <a name="example"></a>Przykład  
 Poniższy kod wykonuje procedurę składowaną, `GetStudentGrades` gdzie `StudentId` jest wymaganym parametrem. Wyniki są następnie odczytywane przez <xref:System.Data.EntityClient.EntityDataReader>.  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>Zobacz także

- [Dostawca EntityClient dla programu Entity Framework](entityclient-provider-for-the-entity-framework.md)
