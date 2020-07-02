---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620317"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="c52ca-101">Nazwa pliku dziennika utworzona przez metodę ObjectContext. isdatabase zmieniła się, aby pasowała do specyfikacji SQL Server</span><span class="sxs-lookup"><span data-stu-id="c52ca-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="c52ca-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c52ca-102">Details</span></span>

<span data-ttu-id="c52ca-103">Gdy <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> Metoda jest wywoływana bezpośrednio lub za pomocą Code First z dostawcą SqlClient i wartością AttachDBFileName w parametrach połączenia, tworzy plik dziennika o nazwie filename_log. ldf zamiast FileName. ldf (gdzie filename to nazwa pliku określonego przez wartość AttachDBFileName).</span><span class="sxs-lookup"><span data-stu-id="c52ca-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="c52ca-104">Ta zmiana usprawnia proces debugowania, dostarczając plik dziennika o nazwie zgodnej ze specyfikacjami programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c52ca-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c52ca-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c52ca-105">Suggestion</span></span>

<span data-ttu-id="c52ca-106">Jeśli nazwa pliku dziennika jest ważna dla aplikacji, należy zaktualizować aplikację, tak aby była oczekiwana standardowa format nazwy pliku _log. ldf.</span><span class="sxs-lookup"><span data-stu-id="c52ca-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="c52ca-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c52ca-107">Name</span></span>    | <span data-ttu-id="c52ca-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="c52ca-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c52ca-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="c52ca-109">Scope</span></span>   |<span data-ttu-id="c52ca-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="c52ca-110">Edge</span></span>|
|<span data-ttu-id="c52ca-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="c52ca-111">Version</span></span>|<span data-ttu-id="c52ca-112">4.5</span><span class="sxs-lookup"><span data-stu-id="c52ca-112">4.5</span></span>|
|<span data-ttu-id="c52ca-113">Typ</span><span class="sxs-lookup"><span data-stu-id="c52ca-113">Type</span></span>|<span data-ttu-id="c52ca-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c52ca-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c52ca-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c52ca-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
