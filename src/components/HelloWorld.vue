<template>
  <v-app class="bgApp" width="100%">
    <v-main class="mt-10 ml-4 main">
      <v-row height="100%" class="d-flex flex-nowrap">
        <draggable :options="options" class="layers">
          <v-col max-height="80%" class=".v-card">
            <v-card color="#ebecf0" width="272px" max-height="800px">
              <div class="py-2">
                <span class="ml-4">TODO (READY)</span>
              </div>

              <draggable
                :list="todos"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card v-for="todo in todos" :todo="todo" :key="todo.id"></user-card>
                <!-- <user-card v-for="todo in todos" :todo="todo" :key="todo.id"></user-card>
                <user-card v-for="todo in todos" :todo="todo" :key="todo.id"></user-card>
                <user-card v-for="todo in todos" :todo="todo" :key="todo.id"></user-card> -->
              </draggable>
            </v-card></v-col
          >
          <v-col>
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">BLOCKING</span>
              </div>

              <draggable
                :list="blocking"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in blocking"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">IN PROGRESS</span>
              </div>

              <draggable
                :list="inProgress"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in inProgress"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">IN CODE REVIEW</span>
              </div>

              <draggable
                :list="codeReview"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in codeReview"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">INSTALLED IN TEST</span>
              </div>

              <draggable
                :list="installedTest"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in installedTest"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">TESTED IN TEST</span>
              </div>

              <draggable
                :list="testedTest"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in testedTest"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>

          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">INSTALLED IN ACC</span>
              </div>

              <draggable
                :list="installedAcc"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in installedTest"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>

          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">TESTED IN ACC (PROD READY)</span>
              </div>

              <draggable
                :list="testedAcc"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in testedAcc"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">DONE (IN PROD)</span>
              </div>

              <draggable
                :list="doneProd"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in doneProd"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">DONE (NO LINK WITH ENV)</span>
              </div>

              <draggable
                :list="doneNoENV"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in doneNoENV"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">BACKLOG (NOT REFINED)</span>
              </div>

              <draggable
                :list="backlog"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in backlog"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">DOCUMENTATION</span>
              </div>

              <draggable
                :list="documentation"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in documentation"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">TECHNICAL DEBT</span>
              </div>

              <draggable
                :list="techDebt"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in techDebt"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
          <v-col height="100%">
            <v-card color="#ebecf0" width="272px">
              <div class="py-2">
                <span class="ml-4">DEPRECATED</span>
              </div>

              <draggable
                :list="deprecated"
                group="people"
                ghostClass="ghost-cls"
                chosenClass="chosen-cls"
                dragClass="drag-cls"
                class="dragArea"
              >
                <user-card
                  v-for="todo in deprecated"
                  :todo="todo"
                  :key="todo.id"
                ></user-card>
              </draggable> </v-card
          ></v-col>
        </draggable>
      </v-row>
    </v-main>
  </v-app>
</template>
<script>
import { VueDraggableNext } from "vue-draggable-next";
//import BaseCard from "./ui/BaseCard.vue";
// import BaseTicket from "./BaseTicketsV2.vue";
import UserCard from "./UserCard";

export default {
  components: {
    draggable: VueDraggableNext,
    //    BaseCard,
    // BaseTicket,
    UserCard,
  },
  data() {
    return {
      enabled: true,
      todos: [
        {
          id: 1,

          description: "Add express checkout to the ecommerce wevsite",
          name: "USER STORY",
          color: "#ff9f1a",
          tag: "mdi-menu",
        },
        {
          id: 2,
          color: "#FF78CB",
          description: "Add Unit tests to the Checkout logic",
          name: "TECHNICAL",
          tag: "s",
        },
        {
          id: 17,

          description: "Add express checkout to the ecommerce wevsite",
          name: "USER STORY",
          color: "#ff9f1a",
          tag: "mdi-menu",
        },
        {
          id: 18,
          color: "#FF78CB",
          description: "Add Unit tests to the Checkout logic",
          name: "TECHNICAL",
          tag: "s",
        },
        {
          id: 19,

          description: "Add express checkout to the ecommerce wevsite",
          name: "USER STORY",
          color: "#ff9f1a",
          tag: "mdi-menu",
        },
        {
          id: 20,
          color: "#FF78CB",
          description: "Add Unit tests to the Checkout logic",
          name: "TECHNICAL",
          tag: "s",
        },
        {
          id: 21,

          description: "Add express checkout to the ecommerce wevsite",
          name: "USER STORY",
          color: "#ff9f1a",
          tag: "mdi-menu",
        },
        {
          id: 22,
          color: "#FF78CB",
          description: "Add Unit tests to the Checkout logic",
          name: "TECHNICAL",
          tag: "s",
        },
        {
          id: 23,

          description: "Add express checkout to the ecommerce wevsite",
          name: "USER STORY",
          color: "#ff9f1a",
          tag: "mdi-menu",
        },
        {
          id: 24,
          color: "#FF78CB",
          description: "Add Unit tests to the Checkout logic",
          name: "TECHNICAL",
          tag: "s",
        },
      ],
      blocking: [
        {
          id: 3,

          description: "Jenkins in TEST doesn't deploy correctly anymore",
          name: "BLOCKED",
          color: "#EB5A46",
          tag: " ",
        },
      ],
      inProgress: [
        {
          id: 4,

          description: "Active Login via Google",
          name: "USER STORY",
          color: "#ff9f1a",
          tag: " ",
        },
        {
          id: 5,
          description: "Issue if login name contains a dot",
          name: "BUG",
          color: "#EB5A46",
          tag: "s",
        },
      ],
      codeReview: [
        {
          id: 6,

          description: "Add integration with instagram",
          name: "USER STORY",
          color: "#ff9f1a",
          tag: " ",
        },
      ],
      installedTest: [
        {
          id: 7,

          description: "Open Friewall rule",
          name: "TECHNICAL",
          color: "#FF78CB",
          tag: " ",
        },
      ],
      testedTest: [],
      installedAcc: [],
      testedAcc: [],
      doneProd: [],
      doneNoENV: [],
      backlog: [
        {
          id: 8,

          description: "Add Discount code functionality",
          name: " ",
          color: "#FF78CB",
          tag: " ",
        },
        {
          id: 9,

          description: "Add products in sales to the catalogue",
          name: "TO DISCUSS",
          color: "#0479BF",
          tag: " ",
        },
      ],
      documentation: [
        {
          id: 10,

          description: "Current Timeline",
          name: " ",
          color: "#FF78CB",
          tag: " ",
        },
        {
          id: 11,

          description: "Relevant Documentation",
          name: " ",
          color: "#0479BF",
          tag: " ",
        },
        {
          id: 12,

          description: "Kickoff meeting",
          name: " ",
          color: "#0479BF",
          tag: " ",
        },
        {
          id: 13,

          description: "_Checklist Templates",
          name: "",
          color: "#0479BF",
          tag: " ",
        },
        {
          id: 14,

          description: "USER STORY",
          name: " USER STORY",
          color: "#ff9f1a",
          tag: " ",
        },
        {
          id: 15,
          description: "BUG",
          name: "BUG",
          color: "#EB5A46",
          tag: "s",
        },
      ],
      techDebt: [
        {
          id: 16,

          description: "Refactor the home page logic",
          name: " ",
          color: "#FF78CB",
          tag: " ",
        },
      ],
      deprecated: [],

      dragging: false,
    };
  },
  methods: {},
};
</script>

<style scoped>
.main {
  overflow-y: hidden !important;
}
.layers {
  display: flex;
}
.v-card {
  overflow: scroll !important;
}
span {
  color: #172b4d;
  font-size: 14px;
}
.bgApp {
  background: url("./background.jpeg");
  background-repeat: no-repeat;
  background-size: 100% 100%;
}
.ticket {
  resize: vertical;
}

.wrapper {
  height: 900px;

  display: grid;
  grid-gap: 5px;

  grid-template-rows: 30px auto;
  grid-template-columns: auto auto auto;
  grid-template-areas:
    "todo-caption wip-caption done-caption"
    "todo wip done";
}

.table-todo {
  grid-area: todo;
  height: 100%;
  border: 1px solid black;
  border-radius: 16px;
  /** /
  background: rgb(255, 150, 150);
  /**/
}

.table-wip {
  grid-area: wip;
  height: 100%;
  border: 1px solid black;
  border-radius: 16px;

  /** /
  background: rgb(140, 210, 255);
  /**/
}

.table-done {
  grid-area: done;
  height: 90%;
  border: 1px solid black;
  border-radius: 16px;
}

/**/
.ghost-cls {
  opacity: 0.3;
  background: rgb(248, 187, 187);
  border-radius: 4px;
  padding: 1rem;
  margin: 0.5rem auto;
  box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.35);
}
/**/

.chosen-cls {
  opacity: 0.6;
  color: rgb(75, 73, 73);
  background: rgb(248, 221, 171);
  border-radius: 4px;
  padding: 1rem;
  margin: 0.5rem auto;
  box-shadow: 2px 2px 8px rgba(50, 50, 50, 0.35);
}

.drag-cls {
  opacity: 0.7;
  background: rgb(190, 252, 190);
  /** / 
  background: rgb(252, 195, 91);
  /**/
  color: rgb(20, 20, 20);
  border-radius: 12px;
  padding: 1rem;
  margin: 0.5rem auto;
  box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.35);
}

.dragArea {
  /**/
  min-height: 20px; /**/
  /**/
  height: 100%;
  /**/
}
/*********************************/
</style>
