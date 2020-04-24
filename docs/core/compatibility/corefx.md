---
title: Podstawowe zmiany w bibliotece klas podstawowych
description: Wyświetla istotne zmiany w podstawowych bibliotekach programu .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 841003fdb114042466cc15b4846e133cf37de85c
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135649"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="bd78f-103">Podstawowe zmiany w bibliotekach .NET</span><span class="sxs-lookup"><span data-stu-id="bd78f-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="bd78f-104">Podstawowe biblioteki .NET zapewniają pierwotne i inne typy ogólne używane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd78f-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="bd78f-105">Następujące istotne zmiany zostały udokumentowane na tej stronie:</span><span class="sxs-lookup"><span data-stu-id="bd78f-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="bd78f-106">Zmiana podziału</span><span class="sxs-lookup"><span data-stu-id="bd78f-106">Breaking change</span></span> | <span data-ttu-id="bd78f-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="bd78f-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="bd78f-108">Interfejsy API służące do raportowania wersji teraz produktu i nie wersji</span><span class="sxs-lookup"><span data-stu-id="bd78f-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="bd78f-109">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-109">3.0</span></span> |
| [<span data-ttu-id="bd78f-110">Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie</span><span class="sxs-lookup"><span data-stu-id="bd78f-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="bd78f-111">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-111">3.0</span></span> |
| [<span data-ttu-id="bd78f-112">Zmiany zachowań formatowania zmiennoprzecinkowego i analizowania</span><span class="sxs-lookup"><span data-stu-id="bd78f-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="bd78f-113">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-113">3.0</span></span> |
| [<span data-ttu-id="bd78f-114">Operacje analizowania zmiennoprzecinkowe nie będą już kończyć się niepowodzeniem lub nie generują wyjątku overflow</span><span class="sxs-lookup"><span data-stu-id="bd78f-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="bd78f-115">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-115">3.0</span></span> |
| [<span data-ttu-id="bd78f-116">InvalidAsynchronousStateException — przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="bd78f-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="bd78f-117">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-117">3.0</span></span> |
| [<span data-ttu-id="bd78f-118">.NET Core 3,0 stosuje się do najlepszych rozwiązań Unicode podczas zamiany nieprawidłowo sformułowanych sekwencji bajtów UTF-8</span><span class="sxs-lookup"><span data-stu-id="bd78f-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="bd78f-119">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-119">3.0</span></span> |
| [<span data-ttu-id="bd78f-120">TypeDescriptionProviderAttribute przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="bd78f-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="bd78f-121">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-121">3.0</span></span> |
| [<span data-ttu-id="bd78f-122">Element ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wpisów</span><span class="sxs-lookup"><span data-stu-id="bd78f-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="bd78f-123">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-123">3.0</span></span> |
| [<span data-ttu-id="bd78f-124">Typ wyjątku serializatora JSON został zmieniony z elementu Jsonexception na NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="bd78f-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="bd78f-125">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-125">3.0</span></span> |
| [<span data-ttu-id="bd78f-126">Zmień semantykę (String) na wartość null w Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="bd78f-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="bd78f-127">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-127">3.0</span></span> |
| [<span data-ttu-id="bd78f-128">Metody JsonEncodedText. Encode mają dodatkowy argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="bd78f-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="bd78f-129">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-129">3.0</span></span> |
| [<span data-ttu-id="bd78f-130">Zmieniono sygnaturę JsonFactoryConverter. isconverter</span><span class="sxs-lookup"><span data-stu-id="bd78f-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="bd78f-131">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-131">3.0</span></span> |
| [<span data-ttu-id="bd78f-132">Zmiany interfejsu API jsonelement</span><span class="sxs-lookup"><span data-stu-id="bd78f-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="bd78f-133">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-133">3.0</span></span> |
| [<span data-ttu-id="bd78f-134">Element FieldInfo. SetValue zgłasza wyjątek dla pól static, tylko init</span><span class="sxs-lookup"><span data-stu-id="bd78f-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="bd78f-135">3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-135">3.0</span></span> |
| [<span data-ttu-id="bd78f-136">Pola prywatne dodane do wbudowanych typów struktur</span><span class="sxs-lookup"><span data-stu-id="bd78f-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="bd78f-137">2.1</span><span class="sxs-lookup"><span data-stu-id="bd78f-137">2.1</span></span> |
| [<span data-ttu-id="bd78f-138">Zmień wartość domyślną UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="bd78f-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="bd78f-139">2.1</span><span class="sxs-lookup"><span data-stu-id="bd78f-139">2.1</span></span> |
| [<span data-ttu-id="bd78f-140">Wersje OpenSSL na macOS</span><span class="sxs-lookup"><span data-stu-id="bd78f-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="bd78f-141">2.1</span><span class="sxs-lookup"><span data-stu-id="bd78f-141">2.1</span></span> |
| [<span data-ttu-id="bd78f-142">UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="bd78f-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="bd78f-143">1.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-143">1.0</span></span> |
| [<span data-ttu-id="bd78f-144">Obsługa wyjątków uszkodzonego stanu procesu nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="bd78f-144">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="bd78f-145">1.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-145">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="bd78f-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bd78f-146">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="bd78f-147">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bd78f-147">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="bd78f-148">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="bd78f-148">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***
