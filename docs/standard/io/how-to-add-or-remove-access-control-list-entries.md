---
title: 'Instrukcje: Dodawanie lub usuwanie pozycji listy kontroli dostępu (tylko program .NET Framework)'
ms.date: 01/14/2019
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
ms.openlocfilehash: 351d8325cc0fc1a1b551b6d513cad02f1291daab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61752063"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="8786c-102">Instrukcje: Dodawanie lub usuwanie pozycji listy kontroli dostępu (tylko program .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="8786c-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="8786c-103">Aby dodać lub usunąć wpisy listy kontroli dostępu (ACL) do lub z pliku lub katalogu, Uzyskaj <xref:System.Security.AccessControl.FileSecurity> lub <xref:System.Security.AccessControl.DirectorySecurity> obiekt z pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="8786c-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="8786c-104">Zmodyfikuj obiekt, a następnie zastosować je do pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="8786c-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="8786c-105">Dodawanie lub usuwanie pozycji listy ACL z pliku</span><span class="sxs-lookup"><span data-stu-id="8786c-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="8786c-106">Wywołaj <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Security.AccessControl.FileSecurity> obiekt, który zawiera bieżące wpisy listy ACL w pliku.</span><span class="sxs-lookup"><span data-stu-id="8786c-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="8786c-107">Dodawanie lub usuwanie pozycji listy ACL z <xref:System.Security.AccessControl.FileSecurity> obiekt zwrócony z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="8786c-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="8786c-108">Aby zastosować zmiany, należy przekazać <xref:System.Security.AccessControl.FileSecurity> obiekt <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8786c-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="8786c-109">Dodawanie lub usuwanie pozycji listy ACL z katalogu</span><span class="sxs-lookup"><span data-stu-id="8786c-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="8786c-110">Wywołaj <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Security.AccessControl.DirectorySecurity> obiekt, który zawiera bieżące wpisy listy ACL w katalogu.</span><span class="sxs-lookup"><span data-stu-id="8786c-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="8786c-111">Dodawanie lub usuwanie pozycji listy ACL z <xref:System.Security.AccessControl.DirectorySecurity> obiekt zwrócony z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="8786c-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="8786c-112">Aby zastosować zmiany, należy przekazać <xref:System.Security.AccessControl.DirectorySecurity> obiekt <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8786c-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8786c-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8786c-113">Example</span></span>  
 <span data-ttu-id="8786c-114">Aby uruchomić ten przykład, należy użyć prawidłowe konto użytkownika lub grupy.</span><span class="sxs-lookup"><span data-stu-id="8786c-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="8786c-115">W przykładzie użyto <xref:System.IO.File> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8786c-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="8786c-116">Użyj tej samej procedury, aby uzyskać <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, i <xref:System.IO.DirectoryInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="8786c-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
