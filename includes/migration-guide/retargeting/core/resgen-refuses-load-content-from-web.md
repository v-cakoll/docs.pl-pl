---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614771"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="20912-101">Resgen odmawia załadowania zawartości z sieci Web</span><span class="sxs-lookup"><span data-stu-id="20912-101">Resgen refuses to load content from the web</span></span>

#### <a name="details"></a><span data-ttu-id="20912-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="20912-102">Details</span></span>

<span data-ttu-id="20912-103">Pliki resx mogą zawierać dane wejściowe w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="20912-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="20912-104">Jeśli spróbujesz użyć Resgen do załadowania pliku pobranego z niezaufanej lokalizacji, domyślnie nie będzie można załadować danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="20912-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="20912-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="20912-105">Suggestion</span></span>

<span data-ttu-id="20912-106">Resgen użytkownicy wymagający ładowania binarnych danych wejściowych z niezaufanych lokalizacji mogą usunąć oznaczenie sieci Web z pliku wejściowego lub zastosować opcję rezygnacji z Quirk. Dodaj następujące ustawienie rejestru, aby zastosować opcję rezygnacji z Quirk: [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;</span><span class="sxs-lookup"><span data-stu-id="20912-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>

| <span data-ttu-id="20912-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="20912-107">Name</span></span>    | <span data-ttu-id="20912-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="20912-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="20912-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="20912-109">Scope</span></span>   | <span data-ttu-id="20912-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="20912-110">Edge</span></span>        |
| <span data-ttu-id="20912-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="20912-111">Version</span></span> | <span data-ttu-id="20912-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="20912-112">4.7.2</span></span>       |
| <span data-ttu-id="20912-113">Typ</span><span class="sxs-lookup"><span data-stu-id="20912-113">Type</span></span>    | <span data-ttu-id="20912-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="20912-114">Retargeting</span></span> |
