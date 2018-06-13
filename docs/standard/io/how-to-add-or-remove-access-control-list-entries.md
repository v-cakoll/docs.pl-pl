---
title: 'Porady: dodawanie lub usuwanie pozycji listy kontroli dostępu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24c428a80f18b35d0aa3119a3c5fa1a6dcb2130e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573426"
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a><span data-ttu-id="4c12a-102">Porady: dodawanie lub usuwanie pozycji listy kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="4c12a-102">How to: Add or Remove Access Control List Entries</span></span>
<span data-ttu-id="4c12a-103">Aby dodać lub usunąć wpisy listy kontroli dostępu (ACL) do lub z pliku, <xref:System.Security.AccessControl.FileSecurity> lub <xref:System.Security.AccessControl.DirectorySecurity> obiektu musi być uzyskane z pliku lub katalogu, modyfikować i następnie stosowane do pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c12a-103">To add or remove Access Control List (ACL) entries to or from a file, the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object must be obtained from the file or directory, modified, and then applied back to the file or directory.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="4c12a-104">Aby dodać lub usunąć wpis listy ACL z pliku</span><span class="sxs-lookup"><span data-stu-id="4c12a-104">To add or remove an ACL entry from a File</span></span>  
  
1.  <span data-ttu-id="4c12a-105">Wywołanie <xref:System.IO.File.GetAccessControl%2A> metodę, aby pobrać <xref:System.Security.AccessControl.FileSecurity> obiekt, który zawiera bieżące wpisy list kontroli dostępu w pliku.</span><span class="sxs-lookup"><span data-stu-id="4c12a-105">Call the <xref:System.IO.File.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2.  <span data-ttu-id="4c12a-106">Dodawanie lub usuwanie pozycji listy ACL z <xref:System.Security.AccessControl.FileSecurity> obiekt zwrócony z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="4c12a-106">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="4c12a-107">Przekaż <xref:System.Security.AccessControl.FileSecurity> do obiektu <xref:System.IO.File.SetAccessControl%2A> metody w celu zastosowania zmian.</span><span class="sxs-lookup"><span data-stu-id="4c12a-107">Pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A> method to apply the changes.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="4c12a-108">Aby dodać lub usunąć wpis listy ACL z katalogu</span><span class="sxs-lookup"><span data-stu-id="4c12a-108">To add or remove an ACL entry from a Directory</span></span>  
  
1.  <span data-ttu-id="4c12a-109">Wywołanie <xref:System.IO.Directory.GetAccessControl%2A> metodę, aby pobrać <xref:System.Security.AccessControl.DirectorySecurity> obiekt, który zawiera bieżące wpisy listy ACL w katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c12a-109">Call the <xref:System.IO.Directory.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2.  <span data-ttu-id="4c12a-110">Dodawanie lub usuwanie pozycji listy ACL z <xref:System.Security.AccessControl.DirectorySecurity> obiekt zwrócony z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="4c12a-110">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="4c12a-111">Przekaż <xref:System.Security.AccessControl.DirectorySecurity> do obiektu <xref:System.IO.Directory.SetAccessControl%2A> metody w celu zastosowania zmian.</span><span class="sxs-lookup"><span data-stu-id="4c12a-111">Pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A> method to apply the changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c12a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c12a-112">Example</span></span>  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4c12a-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4c12a-113">Compiling the Code</span></span>  
 <span data-ttu-id="4c12a-114">Należy podać prawidłowe konto użytkownika lub grupy do uruchomienia tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="4c12a-114">You must supply a valid user or group account to run this example.</span></span> <span data-ttu-id="4c12a-115">W tym przykładzie użyto <xref:System.IO.File> obiektu; jednak służy do tej samej procedury <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, i <xref:System.IO.DirectoryInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="4c12a-115">This example uses a <xref:System.IO.File> object; however, the same procedure is used for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>
