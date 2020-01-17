---
title: Krytyczne zmiany kryptografii — .NET Core
description: Wyświetla listę przerwanych zmian związanych z kryptografią w programie .NET Core.
ms.date: 09/20/2019
ms.openlocfilehash: 4b13985a12ee0530edd3a0960923aafef1696d90
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116467"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="c94b9-103">Krytyczne zmiany kryptografii</span><span class="sxs-lookup"><span data-stu-id="c94b9-103">Cryptography breaking changes</span></span>

<span data-ttu-id="c94b9-104">Następujące istotne zmiany zostały udokumentowane na tej stronie:</span><span class="sxs-lookup"><span data-stu-id="c94b9-104">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="c94b9-105">EnvelopedCms domyślnie szyfrowanie AES-256</span><span class="sxs-lookup"><span data-stu-id="c94b9-105">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption)
- [<span data-ttu-id="c94b9-106">Zwiększono minimalny rozmiar generowania klucza RSAOpenSsl</span><span class="sxs-lookup"><span data-stu-id="c94b9-106">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased)
- [<span data-ttu-id="c94b9-107">.NET Core 3,0 preferuje OpenSSL 1.1. x do OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="c94b9-107">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x)
- [<span data-ttu-id="c94b9-108">Lepsza weryfikacja argumentów w konstruktorze Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="c94b9-108">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor)

## <a name="net-core-30"></a><span data-ttu-id="c94b9-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c94b9-109">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-30-preview-9"></a><span data-ttu-id="c94b9-110">.NET Core 3,0 (wersja zapoznawcza 9)</span><span class="sxs-lookup"><span data-stu-id="c94b9-110">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***
