---
title: Nieobsługiwane interfejsy API w programie .NET Core
description: Dowiedz się, które interfejsy API z .NET Framework, które zawsze zgłaszają wyjątek na platformie .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: f27aeca31226a95dacf100813762eedb56876fbd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936972"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="a310d-103">Interfejsy API, które zawsze generują wyjątki w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="a310d-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="a310d-104">Następujące interfejsy API zawsze będą zgłaszać <xref:System.PlatformNotSupportedException> na platformie .NET Core na wszystkich lub podzestawach platform.</span><span class="sxs-lookup"><span data-stu-id="a310d-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="a310d-105">Ten artykuł organizuje elementy członkowskie interfejsu API według przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a310d-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="a310d-106">Ten artykuł jest pracą w toku.</span><span class="sxs-lookup"><span data-stu-id="a310d-106">This article is a work-in-progress.</span></span> <span data-ttu-id="a310d-107">Nie jest to kompletna lista interfejsów API, które generują wyjątki w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a310d-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="a310d-108">Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, która zgłasza na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a310d-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="a310d-109">Aby uzyskać więcej informacji, zobacz [Serializacja binarna w programie .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="a310d-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="a310d-110">System</span><span class="sxs-lookup"><span data-stu-id="a310d-110">System</span></span>

| <span data-ttu-id="a310d-111">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-111">Member</span></span> | <span data-ttu-id="a310d-112">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-113">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="a310d-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="a310d-115">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="a310d-116">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-117">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="a310d-118">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="a310d-119">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="a310d-120">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-121">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="a310d-122">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="a310d-123">System. CodeDom. Compiler</span><span class="sxs-lookup"><span data-stu-id="a310d-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="a310d-124">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-124">Member</span></span> | <span data-ttu-id="a310d-125">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-126">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-127">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-128">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="a310d-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="a310d-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="a310d-130">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-130">Member</span></span> | <span data-ttu-id="a310d-131">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-132">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-133">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a310d-134">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="a310d-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="a310d-135">System.Configuration</span></span>

| <span data-ttu-id="a310d-136">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-136">Member</span></span> | <span data-ttu-id="a310d-137">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a310d-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="a310d-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="a310d-139">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="a310d-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="a310d-140">System.Console</span></span>

| <span data-ttu-id="a310d-141">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-141">Member</span></span> | <span data-ttu-id="a310d-142">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="a310d-143">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-143">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-145">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-145">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-147">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-147">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-149">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-149">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="a310d-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a310d-151">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-152">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-153">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-154">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-154">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-155"><xref:System.Console.Title?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="a310d-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a310d-156">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-156">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-158">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-158">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-160">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-160">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-162">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-162">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-164">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="a310d-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="a310d-165">System.Data.Common</span></span>

| <span data-ttu-id="a310d-166">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-166">Member</span></span> | <span data-ttu-id="a310d-167">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a310d-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (zgłasza <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="a310d-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="a310d-169">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="a310d-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="a310d-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="a310d-171">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-171">Member</span></span> | <span data-ttu-id="a310d-172">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a310d-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-174">Linux</span><span class="sxs-lookup"><span data-stu-id="a310d-174">Linux</span></span> |
| <span data-ttu-id="a310d-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-176">Linux</span><span class="sxs-lookup"><span data-stu-id="a310d-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="a310d-177">macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="a310d-178">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-179">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="a310d-180">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="a310d-181">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="a310d-182">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="a310d-183">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-183">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-185">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-185">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="a310d-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a310d-187">macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-187">macOS</span></span> |
| <span data-ttu-id="a310d-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-189">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="a310d-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="a310d-190">System.IO</span></span>

| <span data-ttu-id="a310d-191">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-191">Member</span></span> | <span data-ttu-id="a310d-192">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-193">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-194">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="a310d-195">System. IO. Pipes</span><span class="sxs-lookup"><span data-stu-id="a310d-195">System.IO.Pipes</span></span>

| <span data-ttu-id="a310d-196">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-196">Member</span></span> | <span data-ttu-id="a310d-197">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="a310d-198">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="a310d-199">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="a310d-200">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="a310d-201">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-201">Linux and macOS</span></span> |
| <span data-ttu-id="a310d-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-203">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="a310d-204">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="a310d-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="a310d-205">System.Media</span></span>

| <span data-ttu-id="a310d-206">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-206">Member</span></span> | <span data-ttu-id="a310d-207">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-208">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="a310d-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="a310d-209">System.Net</span></span>

| <span data-ttu-id="a310d-210">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-210">Member</span></span> | <span data-ttu-id="a310d-211">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="a310d-212">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="a310d-213">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-214">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-215">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-216">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-217">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-218">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-219">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-220">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-221">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-222">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="a310d-223">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-224">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-225">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-226">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-227">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-228">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="a310d-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="a310d-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="a310d-230">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-230">Member</span></span> | <span data-ttu-id="a310d-231">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-232">Windows (platforma UWP)</span><span class="sxs-lookup"><span data-stu-id="a310d-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="a310d-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="a310d-233">System.Net.Sockets</span></span>

| <span data-ttu-id="a310d-234">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-234">Member</span></span> | <span data-ttu-id="a310d-235">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="a310d-236">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="a310d-237">System .NET. WebSockets</span><span class="sxs-lookup"><span data-stu-id="a310d-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="a310d-238">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-238">Member</span></span> | <span data-ttu-id="a310d-239">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-239">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="a310d-240">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="a310d-241">System. odbicie</span><span class="sxs-lookup"><span data-stu-id="a310d-241">System.Reflection</span></span>

| <span data-ttu-id="a310d-242">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-242">Member</span></span> | <span data-ttu-id="a310d-243">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-243">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-244">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-245">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-246">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a310d-247">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-248">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-249">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="a310d-250">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="a310d-251">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="a310d-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="a310d-252">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-252">Member</span></span> | <span data-ttu-id="a310d-253">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-253">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="a310d-254">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="a310d-255">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="a310d-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="a310d-256">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-256">Member</span></span> | <span data-ttu-id="a310d-257">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-257">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a310d-258">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="a310d-259">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="a310d-260">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="a310d-261">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-262">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="a310d-263">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="a310d-264">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="a310d-265">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="a310d-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="a310d-266">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-266">Member</span></span> | <span data-ttu-id="a310d-267">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-267">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="a310d-268">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="a310d-269">System. Security</span><span class="sxs-lookup"><span data-stu-id="a310d-269">System.Security</span></span>

| <span data-ttu-id="a310d-270">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-270">Member</span></span> | <span data-ttu-id="a310d-271">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-271">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="a310d-272">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="a310d-273">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-274">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="a310d-275">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="a310d-276">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="a310d-277">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="a310d-278">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="a310d-279">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="a310d-280">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="a310d-281">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="a310d-282">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a310d-283">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="a310d-284">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="a310d-285">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="a310d-286">System. Security. Claims</span><span class="sxs-lookup"><span data-stu-id="a310d-286">System.Security.Claims</span></span>

| <span data-ttu-id="a310d-287">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-287">Member</span></span> | <span data-ttu-id="a310d-288">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-288">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="a310d-289">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-290">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="a310d-291">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-292">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-293">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="a310d-294">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="a310d-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="a310d-295">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-295">Member</span></span> | <span data-ttu-id="a310d-296">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-296">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-297">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-298">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="a310d-299">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="a310d-300">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="a310d-301">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="a310d-302">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="a310d-303">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="a310d-304">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="a310d-305">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="a310d-306">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="a310d-307">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="a310d-308">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="a310d-309">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="a310d-310">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a310d-311">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-312">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="a310d-313">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-314">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-315">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-316">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-317">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a310d-318">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-319">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-320">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-321">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="a310d-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-322">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-323">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a310d-324">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a310d-325">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="a310d-326">System. Security. Cryptography. PKCS</span><span class="sxs-lookup"><span data-stu-id="a310d-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="a310d-327">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-327">Member</span></span> | <span data-ttu-id="a310d-328">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="a310d-329">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="a310d-330">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="a310d-331">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="a310d-332">System. Security. Cryptography. x509</span><span class="sxs-lookup"><span data-stu-id="a310d-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="a310d-333">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-333">Member</span></span> | <span data-ttu-id="a310d-334">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-335">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-336">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-337">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-337">All</span></span> |
| <span data-ttu-id="a310d-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="a310d-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a310d-339">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="a310d-340">System. Security. Authentication. Kiedy</span><span class="sxs-lookup"><span data-stu-id="a310d-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="a310d-341">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-341">Member</span></span> | <span data-ttu-id="a310d-342">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-343">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="a310d-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="a310d-344">System.Security.Policy</span></span>

| <span data-ttu-id="a310d-345">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-345">Member</span></span> | <span data-ttu-id="a310d-346">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-347">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="a310d-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="a310d-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="a310d-349">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-349">Member</span></span> | <span data-ttu-id="a310d-350">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-351">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="a310d-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="a310d-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="a310d-353">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-353">Member</span></span> | <span data-ttu-id="a310d-354">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-355">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="a310d-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="a310d-356">System.Threading</span></span>

| <span data-ttu-id="a310d-357">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-357">Member</span></span> | <span data-ttu-id="a310d-358">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-359">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a310d-360">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="a310d-361">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="a310d-362">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="a310d-363">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="a310d-364">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="a310d-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="a310d-365">System.Xml</span></span>

| <span data-ttu-id="a310d-366">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a310d-366">Member</span></span> | <span data-ttu-id="a310d-367">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="a310d-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="a310d-368">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="a310d-369">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="a310d-370">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="a310d-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="a310d-371">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a310d-371">See also</span></span>

- [<span data-ttu-id="a310d-372">Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="a310d-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="a310d-373">Serializacja binarna w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="a310d-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="a310d-374">Analizator przenośności platformy .NET</span><span class="sxs-lookup"><span data-stu-id="a310d-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
