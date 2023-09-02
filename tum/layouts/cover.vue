<script setup lang="ts">
const formatDate = (date) => {
  const options = { year: "numeric", month: "long", day: "numeric" };
  const formattedDate = date.toLocaleDateString("en-US", options);
  const getDaySuffix = (day) => {
    if (day >= 11 && day <= 13) {
      return "th";
    }
    switch (day % 10) {
      case 1:
        return "st";
      case 2:
        return "nd";
      case 3:
        return "rd";
      default:
        return "th";
    }
  };

  // Split the formatted date string to extract day, month, and year
  const parts = formattedDate.split(" ");
  const month = parts[0];
  const day = parseInt(parts[1], 10);
  const daySuffix = getDaySuffix(day);
  const year = parts[2];

  return {
    day,
    daySuffix,
    month,
    year,
  };
};

const presentationDate = formatDate(new Date($slidev.configs.date));
</script>
<template>
  <div class="slidev-layout cover">
    <div class="my-auto w-full">
      <div class="grid grid-cols-2">
        <div>
          <h1>{{ $slidev.configs.title }}</h1>
          <p class="text-tum-blue text-xl">
            {{ $slidev.configs.type }}
          </p>
          <div class="my-12">
            <p class="font-bold">{{ $slidev.configs.author }}</p>
          </div>
          <p>
            Technical University of Munich<br />
            School of Computation, Information and Technology<br />
            Chair for Applied Software Engineering<br />
            {{ presentationDate.month }}
            {{ presentationDate.day }}<sup>{{ presentationDate.daySuffix }}</sup
            >, {{ presentationDate.year }}
          </p>
        </div>
        <img src="../assets/uhrenturm.png" />
      </div>
    </div>
  </div>
</template>
