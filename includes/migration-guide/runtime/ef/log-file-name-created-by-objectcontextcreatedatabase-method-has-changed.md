---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804757"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="b8922-101">Nazwa pliku dziennika, tworzone przez metodę ObjectContext.CreateDatabase został zmieniony na zgodne ze specyfikacjami programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="b8922-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b8922-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b8922-102">Details</span></span>|<span data-ttu-id="b8922-103">Gdy <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> metoda jest wywoływana albo bezpośrednio lub przy użyciu najpierw kod dzięki dostawcy SqlClient i wartość AttachDBFilename w ciągu połączenia, tworzy plik dziennika o nazwie filename_log.ldf zamiast filename.ldf (gdzie nazwa_pliku to nazwa Plik określony przez wartość AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="b8922-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="b8922-104">Ta zmiana usprawnia proces debugowania, dostarczając plik dziennika o nazwie zgodnej ze specyfikacjami programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b8922-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>|
|<span data-ttu-id="b8922-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="b8922-105">Suggestion</span></span>|<span data-ttu-id="b8922-106">Jeśli nazwa pliku dziennika jest ważne w przypadku aplikacji, aplikacji powinny zostać uaktualnione w oczekiwany format nazwy pliku _log.ldf standardowych.</span><span class="sxs-lookup"><span data-stu-id="b8922-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>|
|<span data-ttu-id="b8922-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="b8922-107">Scope</span></span>|<span data-ttu-id="b8922-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="b8922-108">Edge</span></span>|
|<span data-ttu-id="b8922-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="b8922-109">Version</span></span>|<span data-ttu-id="b8922-110">4.5</span><span class="sxs-lookup"><span data-stu-id="b8922-110">4.5</span></span>|
|<span data-ttu-id="b8922-111">Typ</span><span class="sxs-lookup"><span data-stu-id="b8922-111">Type</span></span>|<span data-ttu-id="b8922-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b8922-112">Runtime</span></span>|
|<span data-ttu-id="b8922-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b8922-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
