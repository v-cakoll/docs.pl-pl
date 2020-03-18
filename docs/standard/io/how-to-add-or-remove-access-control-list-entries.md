---
title: 'Sposób: Dodawanie lub usuwanie wpisów listy kontroli dostępu (tylko net framework)'
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
ms.openlocfilehash: 5f41c518b8732adff95593cab29d7085adcc9ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708131"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="1f2c3-102">Sposób: Dodawanie lub usuwanie wpisów listy kontroli dostępu (tylko net framework)</span><span class="sxs-lookup"><span data-stu-id="1f2c3-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="1f2c3-103">Aby dodać lub usunąć wpisy listy kontroli dostępu (ACL) do <xref:System.Security.AccessControl.FileSecurity> lub <xref:System.Security.AccessControl.DirectorySecurity> z pliku lub katalogu, pobierz obiekt lub obiekt z pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="1f2c3-104">Zmodyfikuj obiekt, a następnie zastosuj go z powrotem do pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="1f2c3-105">Dodawanie lub usuwanie wpisu acl z pliku</span><span class="sxs-lookup"><span data-stu-id="1f2c3-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="1f2c3-106">Wywołaj <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metodę, <xref:System.Security.AccessControl.FileSecurity> aby uzyskać obiekt, który zawiera bieżące wpisy acl pliku.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="1f2c3-107">Dodawanie lub usuwanie wpisów <xref:System.Security.AccessControl.FileSecurity> acl z obiektu zwróconego z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="1f2c3-108">Aby zastosować zmiany, <xref:System.Security.AccessControl.FileSecurity> przekaż obiekt <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> do metody.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="1f2c3-109">Dodawanie lub usuwanie wpisu acl z katalogu</span><span class="sxs-lookup"><span data-stu-id="1f2c3-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="1f2c3-110">Wywołaj <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metodę, <xref:System.Security.AccessControl.DirectorySecurity> aby uzyskać obiekt, który zawiera bieżące wpisy acl katalogu.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="1f2c3-111">Dodawanie lub usuwanie wpisów <xref:System.Security.AccessControl.DirectorySecurity> acl z obiektu zwróconego z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="1f2c3-112">Aby zastosować zmiany, <xref:System.Security.AccessControl.DirectorySecurity> przekaż obiekt <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> do metody.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f2c3-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f2c3-113">Example</span></span>  
 <span data-ttu-id="1f2c3-114">Aby uruchomić ten przykład, należy użyć prawidłowego konta użytkownika lub grupy.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="1f2c3-115">W przykładzie <xref:System.IO.File> użyto obiektu.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="1f2c3-116">Użyj tej samej <xref:System.IO.FileInfo>procedury <xref:System.IO.Directory>dla <xref:System.IO.DirectoryInfo> , i klas.</span><span class="sxs-lookup"><span data-stu-id="1f2c3-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
